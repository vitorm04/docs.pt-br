---
title: Escrever um host de tempo de execução personalizado do .NET Core
description: Saiba como hospedar o tempo de execução do .NET Core a partir do código nativo para dar suporte a cenários avançados que exigem o controle de como o tempo de execução do .NET Core funciona.
author: mjrousos
ms.date: 12/21/2018
ms.custom: seodec18
ms.openlocfilehash: 1f04ccfa56c399a4dba003ec0de8a87f888ef848
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849321"
---
# <a name="write-a-custom-net-core-host-to-control-the-net-runtime-from-your-native-code"></a>Escreva um host personalizado do .NET Core para controlar o tempo de execução do .NET a partir de seu código nativo

Como todo código gerenciado, os aplicativos .NET Core são executados por um host. O host é responsável por iniciar o tempo de execução (incluindo componentes como JIT e coletor de lixo) e invocar pontos de entrada gerenciados.

Hospedar o tempo de execução do .NET Core é um cenário avançado e, na maioria dos casos, os desenvolvedores do .NET Core não precisam se preocupar com a hospedagem, pois os processos de build do .NET Core fornecem um host padrão para executar aplicativos .NET Core. No entanto, em algumas circunstâncias especializadas, pode ser útil hospedar explicitamente o tempo de execução do .NET Core, como uma maneira de invocar o código gerenciado em um processo nativo ou para ter mais controle sobre o funcionamento do tempo de execução.

Este artigo fornece uma visão geral das etapas necessárias para iniciar o tempo de execução do .NET Core com base no código nativo e executar o código gerenciado nele.

## <a name="prerequisites"></a>Pré-requisitos

Como os hosts são aplicativos nativos, este tutorial abordará a construção de um aplicativo C++ para hospedar o .NET Core. Você precisará de um ambiente de desenvolvimento do C++ (como aquele fornecido pelo [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)).

Você também desejará ter um aplicativo .NET Core simples com o qual testará o host e, portanto, deverá instalar o [SDK do .NET Core](https://dotnet.microsoft.com/download) e [compilar um aplicativo .NET Core de teste pequeno](with-visual-studio.md) (como um aplicativo “Olá, Mundo”). O aplicativo “Olá, Mundo” criado pelo novo modelo de projeto de console do .NET Core é suficiente.

## <a name="hosting-apis"></a>APIs de hospedagem
Há três APIs diferentes que podem ser usadas para hospedar o .NET Core. Este documento (e seus [exemplos](https://github.com/dotnet/samples/tree/master/core/hosting) associados) abrange todas as opções.

* O método preferencial de hospedar o tempo de execução do .NET Core no .NET Core 3.0 e posteriores é com as APIs das bibliotecas `nethost` e `hostfxr`. Esses pontos de entrada tratam a complexidade de localizar e configurar o tempo de execução para inicialização, bem como permitem iniciar um aplicativo gerenciado e chamar um método gerenciado estático.
* O método preferencial de hospedar o tempo de execução do .NET Core anterior ao .NET Core 3.0 é com a API [CoreClrHost.h](https://github.com/dotnet/coreclr/blob/master/src/coreclr/hosts/inc/coreclrhost.h). Essa API expõe funções para iniciar e interromper facilmente o tempo de execução e invocar o código gerenciado (iniciando um exe gerenciado ou chamando métodos estáticos gerenciados).
* O .NET Core também pode ser hospedado com a interface `ICLRRuntimeHost4` na [mscoree.h](https://github.com/dotnet/coreclr/blob/master/src/pal/prebuilt/inc/mscoree.h). Essa API é mais antiga que a CoreClrHost.h, portanto, talvez você já tenha visto hosts mais antigos usando-a. Ela ainda funciona e permite um pouco mais controle sobre o processo de hospedagem do que a CoreClrHost. No entanto, agora, na maioria dos cenários, a CoreClrHost.h é preferida devido às suas APIs mais simples.

## <a name="sample-hosts"></a>Hosts de exemplo
Há [hosts de exemplo](https://github.com/dotnet/samples/tree/master/core/hosting) que demonstram as etapas descritas nos tutoriais abaixo disponíveis no repositório dotnet/samples do GitHub. Os comentários nos exemplos associam claramente as etapas numeradas destes tutoriais aos pontos em que elas são executadas no exemplo. Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Lembre-se de que os hosts de exemplo devem ser usados para fins de aprendizado e, portanto, não fazem uma verificação de erros rigorosa e são projetados para enfatizar a legibilidade e não a eficiência.

## <a name="create-a-host-using-nethosth-and-hostfxrh"></a>Criar um host usando NetHost.h e HostFxr.h

As etapas a seguir detalham como usar as bibliotecas `nethost` e `hostfxr` para iniciar o tempo de execução do .NET Core em um aplicativo nativo e chamar um método estático gerenciado. A [amostra](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithHostFxr) usa o cabeçalho `nethost`, bem como a biblioteca instalada com o SDK do .NET e cópias dos arquivos [`coreclr_delegates.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/coreclr_delegates.h) e [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) do repositório [dotnet/core-setup](https://github.com/dotnet/core-setup).

### <a name="step-1---load-hostfxr-and-get-exported-hosting-functions"></a>Etapa 1 – Carregar HostFxr e obter funções de hospedagem exportadas

A biblioteca `nethost` fornece a função `get_hostfxr_path` para localizar a biblioteca `hostfxr`. A biblioteca `hostfxr` expõe funções para hospedar o tempo de execução do .NET Core. A lista completa de funções pode ser encontrada em [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) e no [documento de design de hospedagem nativo](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/native-hosting.md). A amostra e este tutorial usam o seguinte:
* `hostfxr_initialize_for_runtime_config`: inicializa um contexto de host e o prepara para a inicialização do tempo de execução do .NET Core usando a configuração de tempo de execução especificada.
* `hostfxr_get_runtime_delegate`: obtém um representante para a funcionalidade de tempo de execução.
* `hostfxr_close`: fecha um contexto de host.

A biblioteca `hostfxr` é encontrada usando `get_hostfxr_path`. Ela é carregada e suas exportações são recuperadas.

[!code-cpp[HostFxrHost#LoadHostFxr](~/samples/core/hosting/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadHostFxr)]

### <a name="step-2---initialize-and-start-the-net-core-runtime"></a>Etapa 2 – Inicializar e iniciar o tempo de execução do .NET Core

As funções `hostfxr_initialize_for_runtime_config` e `hostfxr_get_runtime_delegate` inicializam e iniciam o tempo de execução do .NET Core usando a configuração do tempo de execução para o componente gerenciado que será carregado. A função `hostfxr_get_runtime_delegate` é usada para obter um representante do tempo de execução que permite carregar um assembly gerenciado e obter um ponteiro de função para um método estático no assembly em questão.

[!code-cpp[HostFxrHost#Initialize](~/samples/core/hosting/HostWithHostFxr/src/NativeHost/nativehost.cpp#Initialize)]

### <a name="step-3---load-managed-assembly-and-get-function-pointer-to-a-managed-method"></a>Etapa 3 – Carregar o assembly gerenciado e obter o ponteiro de função para um método gerenciado

O representante do tempo de execução é chamado para carregar o assembly gerenciado e obter um ponteiro de função para um método gerenciado. O representante exige o caminho do assembly, o nome do tipo e o nome do método como entradas e retorna um ponteiro de função que pode ser usado para invocar o método gerenciado.

[!code-cpp[HostFxrHost#LoadAndGet](~/samples/core/hosting/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadAndGet)]

Ao passar `nullptr` como o nome do tipo de representante chamando o representante do tempo de execução, a amostra usa uma assinatura padrão para o método gerenciado:

```csharp
public delegate int ComponentEntryPoint(IntPtr args, int sizeBytes);
```

Uma assinatura diferente pode ser usada especificando o nome do tipo de representante ao chamar o representante do tempo de execução.

### <a name="step-4---run-managed-code"></a>Etapa 4 – Executar o código gerenciado!

O host nativo agora pode chamar o método gerenciado e passar a ele os parâmetros desejados.

[!code-cpp[HostFxrHost#CallManaged](~/samples/core/hosting/HostWithHostFxr/src/NativeHost/nativehost.cpp#CallManaged)]

## <a name="create-a-host-using-coreclrhosth"></a>Criar um host usando a CoreClrHost.h

As etapas a seguir detalham como usar a API CoreClrHost.h para iniciar o tempo de execução do .NET Core em um aplicativo nativo e chamar um método estático gerenciado. Os snippets de código neste documento usam algumas APIs específicas do Windows, mas o [host de exemplo completo](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithCoreClrHost) mostra os caminhos de código do Windows e do Linux.

O [host CoreRun Unix](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/unixcorerun) mostra um exemplo mais complexo e real de hospedar usando coreclrhost.h.

### <a name="step-1---find-and-load-coreclr"></a>Etapa 1 – Localizar e carregar a CoreCLR

As APIs de tempo de execução do .NET Core estão em *coreclr.dll* (no Windows), em *libcoreclr.so* (no Linux) ou em *libcoreclr.dylib* (no macOS). A primeira etapa para hospedar o .NET Core é carregar a biblioteca do CoreCLR. Alguns hosts investigam diferentes caminhos ou usam parâmetros de entrada para localizar a biblioteca, enquanto outros sabem carregá-la de um determinado caminho (por exemplo, próximo ao host ou de um local geral no computador).

Quando encontrada, a biblioteca é carregada com `LoadLibraryEx` (no Windows) ou `dlopen` (no Linux/Mac).

[!code-cpp[CoreClrHost#1](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#1)]

### <a name="step-2---get-net-core-hosting-functions"></a>Etapa 2: Obter funções de hospedagem do .NET Core

A CoreClrHost tem vários métodos importantes úteis para a hospedagem do .NET Core:

* `coreclr_initialize`: inicia o tempo de execução do .NET Core e configura o AppDomain padrão (e único).
* `coreclr_execute_assembly`: executa um assembly gerenciado.
* `coreclr_create_delegate`: cria um ponteiro de função para um método gerenciado.
* `coreclr_shutdown`: desliga o tempo de execução do .NET Core.
* `coreclr_shutdown_2`: como a `coreclr_shutdown`, mas também recupera o código de saída do código gerenciado.

Depois de carregar a biblioteca CoreCLR, a próxima etapa é obter referências a essas funções usando `GetProcAddress` (no Windows) ou `dlsym` (no Linux/Mac).

[!code-cpp[CoreClrHost#2](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#2)]

### <a name="step-3---prepare-runtime-properties"></a>Etapa 3 – Preparar as propriedades do tempo de execução

Antes de iniciar o tempo de execução, é necessário preparar algumas propriedades para especificar o comportamento (especialmente em relação ao carregador de assembly).

As propriedades comuns incluem:

* `TRUSTED_PLATFORM_ASSEMBLIES` Essa é uma lista de caminhos de assembly (delimitada por ";" no Windows e por ":" no Linux) que o tempo de execução poderá resolver por padrão. Alguns hosts têm manifestos embutidos em código que listam os assemblies que eles podem carregar. Outros usuários colocarão uma biblioteca em determinados locais (próximos a *coreclr.dll*, por exemplo) nessa lista.
* `APP_PATHS` Essa é uma lista de caminhos a serem investigados quanto a um assembly se ele não for encontrado na lista de TPA (assemblies de plataforma confiáveis). Como o host tem mais controle sobre quais assemblies são carregados usando a lista de TPA, uma prática recomendada para hosts é determinar quais assemblies eles esperam carregar e listá-los explicitamente. No entanto, se for necessária uma investigação no tempo de execução, essa propriedade poderá permitir esse cenário.
* `APP_NI_PATHS` Essa lista é semelhante à APP_PATHS, exceto que ela foi projetada para conter os caminhos que serão investigados para imagens nativas.
* `NATIVE_DLL_SEARCH_DIRECTORIES` Essa propriedade é uma lista de caminhos que o carregador deverá investigar ao procurar bibliotecas nativas chamadas por meio de p/invoke.
* `PLATFORM_RESOURCE_ROOTS` Essa lista inclui caminhos a serem investigados quanto a assemblies satélite de recursos (em subdiretórios específicos à cultura).

Neste host de exemplo, a lista de TPA é construída simplesmente listando todas as bibliotecas no diretório atual:

[!code-cpp[CoreClrHost#7](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#7)]

Como o exemplo é simples, ele só precisa da propriedade `TRUSTED_PLATFORM_ASSEMBLIES`:

[!code-cpp[CoreClrHost#3](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#3)]

### <a name="step-4---start-the-runtime"></a>Etapa 4 – Iniciar o tempo de execução

Ao contrário da API de hospedagem mscoree.h (descrita abaixo), as APIs CoreCLRHost.h iniciam o tempo de execução e criam o AppDomain padrão, tudo isso com uma única chamada. A função `coreclr_initialize` usa um caminho base, um nome e as propriedades já descritas e retorna um identificador ao host por meio do parâmetro `hostHandle`.

[!code-cpp[CoreClrHost#4](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#4)]

### <a name="step-5---run-managed-code"></a>Etapa 5: Executar o código gerenciado

Com o tempo de execução iniciado, o host pode chamar o código gerenciado. Isso pode ser feito de duas maneiras diferentes. O código de exemplo vinculado a este tutorial usa a função `coreclr_create_delegate` para criar um delegado para um método estático gerenciado. Essa API usa o [nome do assembly](../../framework/app-domains/assembly-names.md), o nome de tipo qualificado pelo namespace e o nome do método como entradas e retorna um delegado que pode ser usado para invocar o método.

[!code-cpp[CoreClrHost#5](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#5)]

Neste exemplo, agora o host pode chamar `managedDelegate` para executar o método `ManagedWorker.DoWork`.

Como alternativa, a função `coreclr_execute_assembly` pode ser usada para iniciar um executável gerenciado. Essa API usa um caminho de assembly e a matriz de argumentos como parâmetros de entrada. Ela carrega o assembly nesse caminho e invoca seu método principal.

```C++
int hr = executeAssembly(
        hostHandle,
        domainId,
        argumentCount,
        arguments,
        "HelloWorld.exe",
        (unsigned int*)&exitCode);
```

### <a name="step-6---shutdown-and-clean-up"></a>Etapa 6 – Desligamento e limpeza

Por fim, quando o host concluir a execução do código gerenciado, o tempo de execução do .NET Core será desligado com `coreclr_shutdown` ou `coreclr_shutdown_2`.

[!code-cpp[CoreClrHost#6](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#6)]

O CoreCLR não oferece suporte à reinicialização ou descarregamento. Não chame `coreclr_initialize` novamente ou descarregue a biblioteca CoreCLR.

## <a name="create-a-host-using-mscoreeh"></a>Criar um host usando Mscoree.h

Como já mencionado, a CoreClrHost.h agora é o método preferencial de hospedar o tempo de execução do .NET Core. A interface `ICLRRuntimeHost4` ainda pode ser usada, no entanto, se as interfaces de CoreClrHost.h não forem suficientes (se os sinalizadores de inicialização não padrão forem necessários, por exemplo, ou se um AppDomainManager for necessário no domínio padrão). Estas instruções mostrarão como hospedar o .NET Core usando a mscoree.h.

O [host CoreRun](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/corerun) mostra um exemplo mais complexo e real de hospedar usando mscoree.h.

### <a name="a-note-about-mscoreeh"></a>Uma observação sobre mscoree.h
A interface de hospedagem `ICLRRuntimeHost4` do .NET Core é definida em [MSCOREE.IDL](https://github.com/dotnet/coreclr/blob/master/src/inc/MSCOREE.IDL). Uma versão de cabeçalho deste arquivo (mscoree.h), que o host precisará referenciar, é produzida por meio da MIDL durante o build do [tempo de execução do .NET Core](https://github.com/dotnet/coreclr/). Se você não desejar compilar o tempo de execução do .NET Core, mscoree.h também estará disponível como um [cabeçalho predefinido](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc) no repositório dotnet/coreclr. Encontre [instruções sobre como compilar o tempo de execução do .NET Core](https://github.com/dotnet/coreclr#building-the-repository) no repositório GitHub.

### <a name="step-1---identify-the-managed-entry-point"></a>Etapa 1 – Identificar o ponto de entrada gerenciado
Depois de referenciar os cabeçalhos necessários ([mscoree.h](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc/mscoree.h) e stdio.h, por exemplo), uma das primeiras coisas que um host do .NET Core deverá fazer é localizar o ponto de entrada gerenciado que será usado. Em nosso host de exemplo, isso é feito apenas usando o primeiro argumento de linha de comando de nosso host como o caminho para um binário gerenciado cujo método `main` será executado.

[!code-cpp[NetCoreHost#1](~/samples/core/hosting/HostWithMscoree/host.cpp#1)]

### <a name="step-2---find-and-load-coreclr"></a>Etapa 2 – Localizar e carregar a CoreCLR
As APIs do tempo de execução do .NET Core estão localizadas em *CoreCLR.dll* (no Windows). Para obter nossa interface de hospedagem (`ICLRRuntimeHost4`), é necessário localizar e carregar *CoreCLR.dll*. É responsabilidade do host definir uma convenção de como ele localizará *CoreCLR.dll*. Alguns hosts esperam que o arquivo esteja presente em um local conhecido em todo o computador (como *%programfiles%\dotnet\shared\Microsoft.NETCore.App\2.1.6*). Outros esperam que *CoreCLR.dll* seja carregado de um local próximo do próprio host ou do aplicativo a ser hospedado. Outros ainda poderão consultar uma variável de ambiente para localizar a biblioteca.

No Linux ou no Mac, a biblioteca básica em tempo de execução é *libcoreclr.so* ou *libcoreclr.dylib*, respectivamente.

Nosso host de exemplo investiga alguns locais comuns para *CoreCLR.dll*. Depois de encontrado, ele deverá ser carregado por meio de `LoadLibrary` (ou `dlopen` no Linux/Mac).

[!code-cpp[NetCoreHost#2](~/samples/core/hosting/HostWithMscoree/host.cpp#2)]

### <a name="step-3---get-an-iclrruntimehost4-instance"></a>Etapa 3 – Obter uma instância de ICLRRuntimeHost4
A interface de hospedagem `ICLRRuntimeHost4` é recuperada pela chamada a `GetProcAddress` (ou `dlsym` no Linux/Mac) em `GetCLRRuntimeHost` e, em seguida, pela invocação dessa função.

[!code-cpp[NetCoreHost#3](~/samples/core/hosting/HostWithMscoree/host.cpp#3)]

### <a name="step-4---set-startup-flags-and-start-the-runtime"></a>Etapa 4 – Configurar sinalizadores de inicialização e iniciar o tempo de execução
Com um `ICLRRuntimeHost4` em mãos, agora podemos especificar sinalizadores de inicialização em todo o tempo de execução e iniciar o tempo de execução. Os sinalizadores de inicialização determinam qual GC (coletor de lixo) será usado (simultâneo ou de servidor), se usaremos um único AppDomain ou vários AppDomains e qual política de otimização do carregador será usada (para o carregamento de assemblies de domínio neutro).

[!code-cpp[NetCoreHost#4](~/samples/core/hosting/HostWithMscoree/host.cpp#4)]

O tempo de execução é iniciado com uma chamada à função `Start`.

```C++
hr = runtimeHost->Start();
```

### <a name="step-5---preparing-appdomain-settings"></a>Etapa 5 – Preparando as configurações de AppDomain
Depois que o tempo de execução for iniciado, é recomendável configurar um AppDomain. Há várias opções que devem ser especificadas durante a criação de um AppDomain do .NET. No entanto, é necessário prepará-lo primeiro.

Os sinalizadores de AppDomain especificam comportamentos de AppDomain relacionados à segurança e interoperabilidade. Os hosts mais antigos do Silverlight usavam essas configurações para restringir o código do usuário a uma área restrita, porém, os hosts do .NET Core mais modernos executam o código do usuário como confiança total e habilitam a interoperabilidade.

[!code-cpp[NetCoreHost#5](~/samples/core/hosting/HostWithMscoree/host.cpp#5)]

Depois de decidir quais sinalizadores AppDomain serão usados, as propriedades de AppDomain deverão ser definidas. As propriedades são pares chave-valor de cadeias de caracteres. Muitas das propriedades estão relacionadas a como o AppDomain carregará os assemblies.

As propriedades comuns de AppDomain incluem:

* `TRUSTED_PLATFORM_ASSEMBLIES` Essa é uma lista de caminhos de assembly (delimitada por `;` no Windows e por `:` no Linux/Mac) para os quais o AppDomain deverá priorizar o carregamento e fornecer confiança total (mesmo em domínios de confiança parcial). Essa lista deve conter assemblies “Framework” e outros módulos confiáveis, semelhante ao GAC em cenários do .NET Framework. Alguns hosts colocarão uma biblioteca próxima a *coreclr.dll* nesta lista, enquanto outros têm manifestos embutidos em código que listam os assemblies confiáveis para suas finalidades.
* `APP_PATHS` Essa é uma lista de caminhos a serem investigados quanto a um assembly se ele não for encontrado na lista de TPA (assemblies de plataforma confiáveis). Como o host tem mais controle sobre quais assemblies são carregados usando a lista de TPA, uma prática recomendada para hosts é determinar quais assemblies eles esperam carregar e listá-los explicitamente. No entanto, se for necessária uma investigação no tempo de execução, essa propriedade poderá permitir esse cenário.
* `APP_NI_PATHS` Essa lista é muito semelhante a APP_PATHS, com exceção de que foi projetada para serem caminhos que serão investigados quanto a imagens nativas.
* `NATIVE_DLL_SEARCH_DIRECTORIES` Essa propriedade é uma lista de caminhos que o carregador deverá investigar ao procurar DLLs nativas chamadas por meio de p/invoke.
* `PLATFORM_RESOURCE_ROOTS` Essa lista inclui caminhos a serem investigados quanto a assemblies satélite de recursos (em subdiretórios específicos à cultura).

Em nosso [host de exemplo simples](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithMscoree), essas propriedades são configuradas da seguinte maneira:

[!code-cpp[NetCoreHost#6](~/samples/core/hosting/HostWithMscoree/host.cpp#6)]

### <a name="step-6---create-the-appdomain"></a>Etapa 6 – Criar o AppDomain
Depois que todos os sinalizadores e as propriedades de AppDomain forem preparados, `ICLRRuntimeHost4::CreateAppDomainWithManager` poderá ser usado para configurar o AppDomain. Opcionalmente, essa função usa um nome de assembly totalmente qualificado e um nome de tipo a ser usado como o gerenciador de AppDomain do domínio. Um gerenciador de AppDomain pode permitir que um host controle alguns aspectos do comportamento de AppDomain e pode fornecer pontos de entrada para iniciar o código gerenciado se o host não pretende invocar o código do usuário diretamente.

[!code-cpp[NetCoreHost#7](~/samples/core/hosting/HostWithMscoree/host.cpp#7)]

### <a name="step-7---run-managed-code"></a>Etapa 7 – Executar o código gerenciado
Com um AppDomain em execução, agora o host pode começar a execução do código gerenciado. A maneira mais fácil de fazer isso é usar `ICLRRuntimeHost4::ExecuteAssembly` para invocar um método de ponto de entrada de um assembly gerenciado. Observe que essa função funciona apenas em cenários de domínio único.

[!code-cpp[NetCoreHost#8](~/samples/core/hosting/HostWithMscoree/host.cpp#8)]

Outra opção, caso `ExecuteAssembly` não atenda às necessidades do host, é usar `CreateDelegate` para criar um ponteiro de função para um método estático gerenciado. Isso exige que o host conheça a assinatura do método na qual ele está chamando (para criar o tipo de ponteiro de função), mas permite aos hosts a flexibilidade de invocar um código diferente de um ponto de entrada de um assembly. O nome do assembly fornecido no segundo parâmetro é o [nome completo do assembly gerenciado](../../framework/app-domains/assembly-names.md) da biblioteca a ser carregada.

```C++
void *pfnDelegate = NULL;
hr = runtimeHost->CreateDelegate(
    domainId,
    L"HW, Version=1.0.0.0, Culture=neutral", // Target managed assembly
    L"ConsoleApplication.Program",           // Target managed type
    L"Main",                                 // Target entry point (static method)
    (INT_PTR*)&pfnDelegate);

((MainMethodFp*)pfnDelegate)(NULL);
```

### <a name="step-8---clean-up"></a>Etapa 8 – Limpar
Por fim, o host deverá executar uma limpeza descarregando AppDomains, interrompendo o tempo de execução e liberando a referência `ICLRRuntimeHost4`.

[!code-cpp[NetCoreHost#9](~/samples/core/hosting/HostWithMscoree/host.cpp#9)]

O CoreCLR não oferece suporte ao descarregamento. Não descarregue a biblioteca CoreCLR.

## <a name="conclusion"></a>Conclusão
Depois que o host for criado, você poderá testá-lo executando-o por meio da linha de comando e passando os argumentos esperados pelo host (como o aplicativo gerenciado a ser executado para o host de exemplo mscoree). Ao especificar o aplicativo .NET Core a ser executado pelo host, lembre-se de usar o arquivo .dll produzido por `dotnet build`. Os executáveis (arquivos .exe) produzidos por `dotnet publish` para aplicativos autossuficientes são, na verdade, o host padrão do .NET Core (para que o aplicativo possa ser iniciado diretamente na linha de comando nos principais cenários). O código de usuário é compilado em uma dll com o mesmo nome.

Se as coisas não funcionarem no começo, verifique novamente se *coreclr.dll* está disponível no local esperado pelo host, se todas as bibliotecas do Framework necessárias estão na lista de TPA e se o número de bit de CoreCLR (32 ou 64 bits) corresponde a como o host foi compilado.

A hospedagem do tempo de execução do .NET Core é um cenário avançado do qual muitos desenvolvedores não precisarão. No entanto, para aqueles que precisam inicializar o código gerenciado de um processo nativo ou que precisam de mais controle sobre o comportamento do tempo de execução do .NET Core, ela pode ser muito útil.
