---
title: Hospedando o .NET Core | Microsoft Docs
description: "Hospedando o tempo de execução do .NET Core com base no código nativo"
keywords: .NET, .NET Core, Hospedagem, Hospedando o .NET Core
author: mjrousos
ms.author: mikerou
ms.date: 2/3/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 13edec8b-614d-47ed-9e95-ed6d3b94ec0c
ms.translationtype: Human Translation
ms.sourcegitcommit: d866cf8eab2b8db936d813ccae7882f8d7db5720
ms.openlocfilehash: cf420d4379afbdb3c6db048c7817a4c143c124d9
ms.contentlocale: pt-br
ms.lasthandoff: 04/26/2017

---

# <a name="hosting-net-core"></a>Hospedando o .NET Core

Como todo código gerenciado, os aplicativos .NET Core são executados por um host. O host é responsável por iniciar o tempo de execução (incluindo componentes como JIT e coletor de lixo), criar AppDomains e invocar pontos de entrada gerenciados.

Hospedar o tempo de execução do .NET Core é um cenário avançado e, na maioria dos casos, os desenvolvedores do .NET Core não precisam se preocupar com a hospedagem, pois os processos de build do .NET Core fornecem um host padrão para executar aplicativos .NET Core. No entanto, em algumas circunstâncias especializadas, pode ser útil hospedar explicitamente o tempo de execução do .NET Core, como uma maneira de invocar o código gerenciado em um processo nativo ou para ter mais controle sobre o funcionamento do tempo de execução.

Este artigo fornece uma visão geral das etapas necessárias para iniciar o tempo de execução do .NET Core com base no código nativo, criar um domínio do aplicativo inicial (<xref:System.AppDomain>) e executar o código gerenciado nele.

## <a name="prerequisites"></a>Pré-requisitos

Como os hosts são aplicativos nativos, este tutorial abordará a construção de um aplicativo C++ para hospedar o .NET Core. Você precisará de um ambiente de desenvolvimento do C++ (como aquele fornecido pelo [Visual Studio](https://www.visualstudio.com/downloads/)).

Você também desejará ter um aplicativo .NET Core simples com o qual testará o host e, portanto, deverá instalar o [SDK do .NET Core](https://www.microsoft.com/net/core) e [compilar um aplicativo .NET Core de teste pequeno](../../csharp/getting-started/with-visual-studio.md) (como um aplicativo “Olá, Mundo”). O aplicativo “Olá, Mundo” criado pelo novo modelo de projeto de console do .NET Core é suficiente.

Este tutorial e seu exemplo associado criam um host do Windows, consulte as notas ao final deste artigo sobre a hospedagem no UNIX.

## <a name="creating-the-host"></a>Criando o host

Um [host de exemplo](https://github.com/dotnet/docs/tree/master/samples/core/hosting) que demonstra as etapas descritas neste artigo está disponível no repositório dotnet/docs do GitHub. Os comentários no arquivo *host.cpp* do exemplo associam claramente as etapas numeradas deste tutorial aos pontos em que são executadas no exemplo. Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Lembre-se de que o host de exemplo destina-se a ser usado para fins de aprendizado e, portanto, não leva a sério a verificação de erros e é projetado para enfatizar a legibilidade em detrimento da eficiência. Mais amostras de host do mundo real estão disponíveis no repositório [dotnet/coreclr](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts). O [host CoreRun](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/corerun), em particular, é um bom host de uso geral para ser estudado depois de ler toda a amostra mais simples.

### <a name="a-note-about-mscoreeh"></a>Uma observação sobre mscoree.h
A interface de hospedagem primária do .NET Core (`ICLRRuntimeHost2`) é definida em [MSCOREE.IDL](https://github.com/dotnet/coreclr/blob/master/src/inc/MSCOREE.IDL). Uma versão de cabeçalho deste arquivo (mscoree.h), que o host precisará referenciar, é produzida por meio da MIDL durante o build do [tempo de execução do .NET Core](https://github.com/dotnet/coreclr/). Se você não desejar compilar o tempo de execução do .NET Core, mscoree.h também estará disponível como um [cabeçalho predefinido](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc) no repositório dotnet/coreclr. Encontre [instruções sobre como compilar o tempo de execução do .NET Core](https://github.com/dotnet/coreclr#building-the-repository) no repositório GitHub. 

### <a name="step-1---identify-the-managed-entry-point"></a>Etapa 1 – Identificar o ponto de entrada gerenciado
Depois de referenciar os cabeçalhos necessários ([mscoree.h](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc/mscoree.h) e stdio.h, por exemplo), uma das primeiras coisas que um host do .NET Core deverá fazer é localizar o ponto de entrada gerenciado que será usado. Em nosso host de exemplo, isso é feito apenas usando o primeiro argumento de linha de comando de nosso host como o caminho para um binário gerenciado cujo método `main` será executado.

[!code-cpp[NetCoreHost#1](../../../samples/core/hosting/host.cpp#1)]

### <a name="step-2---find-and-load-coreclrdll"></a>Etapa 2 – Localizar e carregar CoreCLR.dll
As APIs do tempo de execução do .NET Core estão localizadas em *CoreCLR.dll* (no Windows). Para obter nossa interface de hospedagem (`ICLRRuntimeHost2`), é necessário localizar e carregar *CoreCLR.dll*. É responsabilidade do host definir uma convenção de como ele localizará *CoreCLR.dll*. Alguns hosts esperam que o arquivo esteja presente em um local conhecido em todo o computador (como %programfiles%\dotnet\shared\Microsoft.NETCore.App\1.1.0). Outros esperam que *CoreCLR.dll* seja carregado de um local próximo do próprio host ou do aplicativo a ser hospedado. Outros ainda poderão consultar uma variável de ambiente para localizar a biblioteca.

No Linux ou no Mac, a biblioteca básica em tempo de execução é *libcoreclr.so* ou *libcoreclr.dylib*, respectivamente.

Nosso host de exemplo investiga alguns locais comuns para *CoreCLR.dll*. Depois de encontrado, ele deverá ser carregado por meio de `LoadLibrary` (ou `dlopen` no Linux/Mac).

[!code-cpp[NetCoreHost#2](../../../samples/core/hosting/host.cpp#2)]

### <a name="step-3---get-an-iclrruntimehost2-instance"></a>Etapa 3 – Obter uma instância de ICLRRuntimeHost2
A interface de hospedagem `ICLRRuntimeHost2` é recuperada pela chamada a `GetProcAddress` (ou `dlsym` no Linux/Mac) em `GetCLRRuntimeHost` e, em seguida, pela invocação dessa função. 

[!code-cpp[NetCoreHost#3](../../../samples/core/hosting/host.cpp#3)]

### <a name="step-4---setting-startup-flags-and-starting-the-runtime"></a>Etapa 4 – Configurando sinalizadores de inicialização e iniciando o tempo de execução
Com um `ICLRRuntimeHost2` em mãos, agora podemos especificar sinalizadores de inicialização em todo o tempo de execução e iniciar o tempo de execução. Os sinalizadores de inicialização determinarão qual GC (coletor de lixo) será usado (simultâneo ou de servidor), se usaremos um AppDomain único ou vários AppDomains e qual política de otimização do carregador será usada (para o carregamento de domínio neutro de assemblies).

[!code-cpp[NetCoreHost#4](../../../samples/core/hosting/host.cpp#4)]

O tempo de execução é iniciado com uma chamada à função `Start`.

```C++
hr = runtimeHost->Start();
```

### <a name="step-5---preparing-appdomain-settings"></a>Etapa 5 – Preparando as configurações de AppDomain
Depois que o tempo de execução for iniciado, é recomendável configurar um AppDomain. Há várias opções que devem ser especificadas durante a criação de um AppDomain do .NET. No entanto, é necessário prepará-lo primeiro.

Os sinalizadores de AppDomain especificam comportamentos de AppDomain relacionados à segurança e interoperabilidade. Os hosts mais antigos do Silverlight usavam essas configurações para restringir o código do usuário a uma área restrita, porém, os hosts do .NET Core mais modernos executam o código do usuário como confiança total e habilitam a interoperabilidade.

[!code-cpp[NetCoreHost#5](../../../samples/core/hosting/host.cpp#5)]

Depois de decidir quais sinalizadores AppDomain serão usados, as propriedades de AppDomain deverão ser definidas. As propriedades são pares chave-valor de cadeias de caracteres. Muitas das propriedades estão relacionadas a como o AppDomain carregará os assemblies.

As propriedades comuns de AppDomain incluem:

* `TRUSTED_PLATFORM_ASSEMBLIES` Essa é uma lista de caminhos de assembly (delimitada por “;” no Windows e por “:” no Unix) para os quais o AppDomain deverá priorizar o carregamento e fornecer confiança total (mesmo em domínios de confiança parcial). Essa lista deve conter assemblies “Framework” e outros módulos confiáveis, semelhante ao GAC em cenários do .NET Framework. Alguns hosts colocarão uma biblioteca próxima a *coreclr.dll* nesta lista, enquanto outros têm manifestos embutidos em código que listam os assemblies confiáveis para suas finalidades.
* `APP_PATHS` Essa é uma lista de caminhos a serem investigados quanto a um assembly se ele não for encontrado na lista de TPA (assemblies de plataforma confiáveis). Esses caminhos devem ser os locais em que os assemblies dos usuários podem ser encontrados. Em um AppDomain em área restrita, os assemblies carregados desses caminhos só receberão confiança parcial. Caminhos APP_PATH comuns incluem o caminho do qual o aplicativo de destino foi carregado ou outros locais em que os ativos do usuário são conhecidos como dinâmicos.
*  `APP_NI_PATHS` Essa lista é muito semelhante a APP_PATHS, com exceção de que foi projetada para serem caminhos que serão investigados quanto a imagens nativas.
*  `NATIVE_DLL_SEARCH_DIRECTORIES` Essa propriedade é uma lista de caminhos que o carregador deverá investigar ao procurar DLLs nativas chamadas por meio de p/invoke.
*  `PLATFORM_RESOURCE_ROOTS` Essa lista inclui caminhos a serem investigados quanto a assemblies satélite de recursos (em subdiretórios específicos à cultura).
*  `AppDomainCompatSwitch` Essa cadeia de caracteres especifica quais particularidades de compatibilidade deverão ser usadas para assemblies sem um Moniker de Estrutura de Destino explícito (um atributo no nível de assembly que indica em qual Estrutura um assembly deve ser executado). Normalmente, isso deve ser definido como `"UseLatestBehaviorWhenTFMNotSpecified"`, mas alguns hosts podem preferir obter particularidades de compatibilidade do Silverlight ou do Windows Phone mais antigas.

Em nosso [host de exemplo simples](https://github.com/dotnet/docs/tree/master/samples/core/hosting), essas propriedades são configuradas da seguinte maneira:

[!code-cpp[NetCoreHost#6](../../../samples/core/hosting/host.cpp#6)]

### <a name="step-6---create-the-appdomain"></a>Etapa 6 – Criar o AppDomain
Depois que todos os sinalizadores e as propriedades de AppDomain forem preparados, `ICLRRuntimeHost2::CreateAppDomainWithManager` poderá ser usado para configurar o AppDomain. Opcionalmente, essa função usa um nome de assembly totalmente qualificado e um nome de tipo a ser usado como o gerenciador de AppDomain do domínio. Um gerenciador de AppDomain pode permitir que um host controle alguns aspectos do comportamento de AppDomain e pode fornecer pontos de entrada para iniciar o código gerenciado se o host não pretende invocar o código do usuário diretamente.   

[!code-cpp[NetCoreHost#7](../../../samples/core/hosting/host.cpp#7)]

### <a name="step-7---run-managed-code"></a>Etapa 7 – Executar o código gerenciado
Com um AppDomain em execução, agora o host pode começar a execução do código gerenciado. A maneira mais fácil de fazer isso é usar `ICLRRuntimeHost2::ExecuteAssembly` para invocar um método de ponto de entrada de um assembly gerenciado. Observe que essa função funciona apenas em cenários de domínio único.

[!code-cpp[NetCoreHost#8](../../../samples/core/hosting/host.cpp#8)]

Outra opção, caso `ExecuteAssembly` não atenda às necessidades do host, é usar `CreateDelegate` para criar um ponteiro de função para um método estático gerenciado. Isso exige que o host conheça a assinatura do método na qual ele está chamando (para criar o tipo de ponteiro de função), mas permite aos hosts a flexibilidade de invocar um código diferente de um ponto de entrada de um assembly.

```C++
void *pfnDelegate = NULL;
hr = runtimeHost->CreateDelegate(
  domainId,
  L"HW, Version=1.0.0.0, Culture=neutral",    // Target managed assembly
  L"ConsoleApplication.Program",            // Target managed type
  L"Main",                                    // Target entry point (static method)
  (INT_PTR*)&pfnDelegate);

((MainMethodFp*)pfnDelegate)(NULL);
```

### <a name="step-8---clean-up"></a>Etapa 8 – Limpar
Por fim, o host deverá executar uma limpeza descarregando AppDomains, interrompendo o tempo de execução e liberando a referência `ICLRRuntimeHost2`.

[!code-cpp[NetCoreHost#9](../../../samples/core/hosting/host.cpp#9)]

## <a name="about-hosting-net-core-on-unix"></a>Sobre a hospedagem do .NET Core no Unix
O .NET Core é um produto de plataforma cruzada, em execução em sistemas operacionais Windows, Linux e Mac. No entanto, como aplicativos nativos, os hosts de diferentes plataformas terão algumas diferenças entre si. O processo descrito acima de como usar `ICLRRuntimeHost2` para iniciar o tempo de execução, criar um AppDomain e executar o código gerenciado deve funcionar em qualquer sistema operacional com suporte. No entanto, as interfaces definidas em mscoree.h podem ser difíceis de serem trabalhadas em plataformas Unix, já que mscoree faz várias suposições do Win32.

Para facilitar a hospedagem em plataformas Unix, um conjunto de wrappers de API de hospedagem mais de plataforma neutra está disponível em [coreclrhost.h](https://github.com/dotnet/coreclr/blob/master/src/coreclr/hosts/inc/coreclrhost.h).

Veja um exemplo de como usar coreclrhost.h (em vez de usar mscoree.h diretamente) no [host UnixCoreRun](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts). As etapas para usar as APIs de coreclrhost.h para hospedar o tempo de execução são semelhantes às etapas de como usar mscoree.h:

1. Identifique o código gerenciado a ser executado (em parâmetros de linha de comando, por exemplo). 
2. Carregue a biblioteca de CoreCLR.
    1. `dlopen("./libcoreclr.so", RTLD_NOW | RTLD_LOCAL);` 
3. Obtenha ponteiros de função para as funções `coreclr_initialize`, `coreclr_create_delegate`, `coreclr_execute_assembly` e `coreclr_shutdown` de CoreCLR usando `dlsym`
    1. `coreclr_initialize_ptr coreclr_initialize = (coreclr_initialize_ptr)dlsym(coreclrLib, "coreclr_initialize");`
4. Configure as propriedades de AppDomain (como a lista de TPA). Isso é o mesmo que a etapa 5 do fluxo de trabalho de mscoree acima.
5. Use `coreclr_initialize` para iniciar o tempo de execução e criar um AppDomain. Isso também criará um ponteiro `hostHandle` que será usado em futuras chamadas de hospedagem.
    1. Observe que essa função executa as funções das etapas 4 e 6 do fluxo de trabalho anterior. 
6. Use `coreclr_execute_assembly` ou `coreclr_create_delegate` para executar o código gerenciado. Essas funções são análogas às funções `ExecuteAssembly` e `CreateDelegate` de mscoree da etapa 7 do fluxo de trabalho anterior.
7. Use `coreclr_shutdown` para descarregar o AppDomain e desligar o tempo de execução. 

## <a name="conclusion"></a>Conclusão
Depois de compilar o host, é possível testá-lo executando-o por meio da linha de comando e passando argumentos (como o aplicativo gerenciado a ser executado) esperados pelo host. Ao especificar o aplicativo .NET Core a ser executado pelo host, lembre-se de usar o arquivo .dll produzido por `dotnet build`. Executáveis produzidos por `dotnet publish` para aplicativos independentes são, na verdade, o host padrão do .NET Core (para que o aplicativo possa ser iniciado diretamente na linha de comando nos principais cenários); o código de usuário é compilado em uma dll com o mesmo nome. 

Se as coisas não funcionarem no começo, verifique novamente se *coreclr.dll* está disponível no local esperado pelo host, se todas as bibliotecas do Framework necessárias estão na lista de TPA e se o número de bit de CoreCLR (32 ou 64 bits) corresponde a como o host foi compilado.

A hospedagem do tempo de execução do .NET Core é um cenário avançado do qual muitos desenvolvedores não precisarão. No entanto, para aqueles que precisam inicializar o código gerenciado de um processo nativo ou que precisam de mais controle sobre o comportamento do tempo de execução do .NET Core, ela pode ser muito útil. Como o .NET Core pode ser executado lado a lado consigo mesmo, é possível até mesmo criar hosts que inicializam e iniciam várias versões do tempo de execução do .NET Core e executam aplicativos em todos eles no mesmo processo. 

