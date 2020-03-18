---
title: Assemblies no .NET
ms.date: 08/15/2019
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
helpviewer_keywords:
- dynamic assemblies
- security [.NET Framework], boundaries
- boundaries of assemblies
- assemblies [.NET Framework], about
- assemblies [.NET Framework], boundaries
- reference scope boundaries
- assemblies [.NET Framework]
- version boundaries
- type boundaries
ms.openlocfilehash: f85fef37ac952c91ac73570f26d80d8a46f4eedf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156499"
---
# <a name="assemblies-in-net"></a>Assemblies no .NET

Os conjuntos formam as unidades fundamentais de implantação, controle de versão, reutilização, escopo de ativação e permissões de segurança para . Aplicativos baseados em NET. Um assembly é uma coleção de tipos e recursos compilados para funcionar juntos e formar uma unidade lógica de funcionalidade. As assembléias assumem a forma de arquivos executáveis *(.exe)* ou dynamic link library *(.dll),* e são os blocos de construção de aplicativos .NET. Eles oferecem ao Common Language Runtime as informações de que ele precisa para estar ciente das implementações de tipo.

No .NET Core e no .NET Framework, você pode construir um conjunto a partir de um ou mais arquivos de código-fonte. No .NET Framework, os assemblies podem conter um ou mais módulos. Isso permite que projetos maiores sejam planejados para que vários desenvolvedores possam trabalhar em arquivos ou módulos de código-fonte separados, que são combinados para criar um único conjunto. Para obter mais informações sobre módulos, consulte [Como: Construir um conjunto de arquivos múltiplos](../../framework/app-domains/build-multifile-assembly.md).

Os assemblies têm as seguintes propriedades:

- Os conjuntos são implementados como *arquivos .exe* ou *.dll.*

- Para bibliotecas que visam o .NET Framework, você pode compartilhar conjuntos entre aplicativos colocando-os no [cache de montagem global (GAC)](../../framework/app-domains/gac.md). Você deve fazer montagens de nomes fortes antes de incluí-las no GAC. Para obter mais informações, consulte [montagens com nome forte](strong-named.md).

- Os assemblies serão carregados na memória somente se forem necessários. Se não forem usados, não estão carregados. Isso significa que os assemblies podem ser uma maneira eficiente de gerenciar recursos em projetos grandes.

- Você pode obter informações programaticamente sobre um assembly usando reflexão. Para obter mais informações, confira [Reflexão (C#)](../../csharp/programming-guide/concepts/reflection.md) ou [Reflexão (Visual Basic)](../../visual-basic/programming-guide/concepts/reflection.md).

- Você pode carregar um conjunto apenas <xref:System.Reflection.MetadataLoadContext> para inspecioná-lo <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> usando a classe em .NET Core e os métodos ou em .NET Core e .NET Framework.

## <a name="assemblies-in-the-common-language-runtime"></a>Assembléias no tempo de execução da língua comum

Os conjuntos fornecem o tempo de execução do idioma comum com as informações que ele precisa estar ciente das implementações do tipo. Para o runtime, um tipo não existe fora do contexto de um assembly.

Uma montagem define as seguintes informações:

- Código que o tempo de execução da linguagem comum executa. Observe que cada montagem pode ter `DllMain` `WinMain`apenas `Main`um ponto de entrada: , ou .

- Limite de segurança. Um assembly é a unidade na qual as permissões são solicitadas e concedidas. Para obter mais informações sobre os limites de segurança nas assembléias, consulte [considerações de segurança da Assembléia](security-considerations.md).

- Tipo limite. A identidade de cada tipo inclui o nome do assembly no qual ele reside. Um tipo chamado `MyType`, carregado no escopo de um assembly, não é o mesmo de um tipo chamado `MyType`, carregado no escopo de outro assembly.

- Limite de escopo de referência. O [manifesto de montagem](#assembly-manifest) possui metadados que são usados para resolver tipos e satisfazer solicitações de recursos. O manifesto especifica os tipos e recursos para expor fora da montagem, e enumera outras assembléias das quais depende. O código de linguagem intermediária da Microsoft (MSIL) em um arquivo executável portátil (PE) não será executado a menos que tenha um manifesto de [montagem](#assembly-manifest)associado .

- Limite de versão. O conjunto é a menor unidade versável no tempo de execução do idioma comum. Todos os tipos e recursos no mesmo conjunto são versios como uma unidade. O [manifesto de montagem](#assembly-manifest) descreve as dependências de versão especificadas para quaisquer assembléias dependentes. Para obter mais informações sobre a versão, consulte [versão do Assembly](versioning.md).

- Unidade de implantação. Quando um aplicativo é iniciado, somente os assemblies que o aplicativo chama inicialmente devem estar presentes. Outras montagens, como montagens contendo recursos de localização ou classes de utilidades, podem ser recuperadas demanda. Isso permite que os aplicativos sejam simples e finos quando baixados pela primeira vez. Para obter mais informações sobre a implantação de conjuntos, consulte [Implantar aplicativos](../../framework/deployment/index.md).

- Unidade de execução lado a lado. Para obter mais informações sobre a execução de várias versões de um conjunto, consulte [Assembléias e execução lado a lado](side-by-side-execution.md).

## <a name="create-an-assembly"></a>Criar uma montagem

Assemblies podem ser estáticos ou dinâmicos. Assemblies estáticos são armazenados em disco em arquivos PE. Os conjuntos estáticos podem incluir interfaces, classes e recursos, como bitmaps, arquivos JPEG e outros arquivos de recursos. Você também pode criar conjuntos dinâmicos, que são executados diretamente da memória e não são salvos em disco antes da execução. Você pode salvar assemblies dinâmicos em disco após sua execução.

Existem várias maneiras de criar assemblies. Você pode usar ferramentas de desenvolvimento, como o Visual Studio, que podem criar arquivos *.dll* ou *.exe.* Você pode usar ferramentas no Windows SDK para criar conjuntos com módulos de outros ambientes de desenvolvimento. Você também pode usar APIs do Common Language Runtime, como <xref:System.Reflection.Emit?displayProperty=nameWithType>, a fim de criar assemblies dinâmicos.

Compile montagens construindo-as no Visual Studio, construindo-as com ferramentas de interface de linha de comando .NET Core ou construindo conjuntos .NET Framework com um compilador de linha de comando. Para obter mais informações sobre a construção de montagens usando o .NET Core CLI, consulte [a visão geral do .NET Core CLI](../../core/tools/index.md). Para construir montagens com os compiladores de linha de comando, consulte [compilação de linha de comando com csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) para C#, ou [Build a partir da linha de comando](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) para Visual Basic.

> [!NOTE]
> Para construir um conjunto no Visual Studio, no menu **Build,** selecione **Build**.

## <a name="assembly-manifest"></a>Manifesto do assembly

Cada assembléia tem um *arquivo manifesto de montagem.* Semelhante a uma tabela de conteúdo, o manifesto de montagem contém:

- A identidade do assembly (seu nome e versão).

- Uma tabela de arquivos descrevendo todos os outros arquivos que compõem o conjunto, como outros conjuntos que você criou que seu arquivo *.exe* ou *.dll* conta, arquivos bitmap ou arquivos Readme.

- Uma *lista de referência de montagem*, que é uma lista de todas as dependências externas, como *.dll*s ou outros arquivos. As referências de assembly contêm referências a objetos globais e privados. Os objetos globais estão disponíveis para todos os outros aplicativos. No .NET Core, os objetos globais são acoplados a um tempo de execução do .NET Core particular. No .NET Framework, os objetos globais residem no cache de montagem global (GAC). *System.IO.dll* é um exemplo de montagem no GAC. Objetos privados devem estar em um nível de diretório em ou abaixo do diretório em que seu aplicativo está instalado.

Como os conjuntos contêm informações sobre conteúdo, versões e dependências, os aplicativos que os usam não precisam depender de fontes externas, como o registro em sistemas Windows, para funcionar corretamente. Os conjuntos reduzem os conflitos *.dll* e tornam seus aplicativos mais confiáveis e fáceis de implantar. Em muitos casos, você pode instalar um aplicativo baseado em .NET simplesmente copiando seus arquivos para o computador de destino. Para obter mais informações, consulte [o manifesto da Assembléia](manifest.md).

## <a name="add-a-reference-to-an-assembly"></a>Adicione uma referência a um conjunto

Para usar um conjunto em um aplicativo, você deve adicionar uma referência a ele. Uma vez que um conjunto é referenciado, todos os tipos acessíveis, propriedades, métodos e outros membros de seus namespaces estão disponíveis para o seu aplicativo como se seu código fosse parte do seu arquivo de origem.

> [!NOTE]
> A maioria dos assemblies da Biblioteca de Classes .NET é referenciada automaticamente. Se um conjunto de sistemas não for automaticamente referenciado, para .NET Core, você poderá adicionar uma referência ao pacote NuGet que contém o conjunto. Use o NuGet Package Manager no Visual [ \<](../../core/tools/dependencies.md#the-packagereference-element) Studio ou adicione um elemento de>PackageReference para a montagem ao projeto *.csproj* ou *.vbproj.* No .NET Framework, você pode adicionar uma referência ao conjunto usando a caixa `-reference` de diálogo Adicionar **referência** no Visual Studio ou usando a opção de linha de comando para os compiladores [C#](../../csharp/language-reference/compiler-options/reference-compiler-option.md) ou [Visual Basic.](../../visual-basic/reference/command-line-compiler/reference.md)

Em C#, você pode usar duas versões do mesmo conjunto em um único aplicativo. Para obter mais informações, consulte [alias externo](../../csharp/language-reference/keywords/extern-alias.md).

## <a name="related-content"></a>Conteúdo relacionado

|Title|Descrição|
|-----------|-----------------|
|[Conteúdos do assembly](contents.md)|Elementos que compõem uma montagem.|
|[Manifesto de assembléia](manifest.md)|Dados no manifesto de montagem, e como são armazenados em conjuntos.|
|[Cache de montagem global](../../framework/app-domains/gac.md)|Como o GAC armazena e usa montagens.|
|[Assembléias com nomes fortes](strong-named.md)|Características de assembléias de nome forte.|
|[Considerações sobre a segurança do assembly](security-considerations.md)|Como a segurança funciona com as assembléias.|
|[Controle de versão do assembly](versioning.md)|Visão geral da diretiva de versão .NET Framework.|
|[Colocação da montagem](../../framework/app-domains/assembly-placement.md)|Onde localizar montagens.|
|[Assemblies e execução lado a lado](side-by-side-execution.md)|Use várias versões do tempo de execução ou de um conjunto simultaneamente.|
|[Emissão de métodos e assemblies dinâmicos](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|Como criar conjuntos dinâmicos.|
|[Como o tempo de execução localiza conjuntos](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|Como o Quadro .NET resolve as referências de montagem em tempo de execução.|

## <a name="reference"></a>Referência

<xref:System.Reflection.Assembly?displayProperty=nameWithType>

## <a name="see-also"></a>Confira também

- [Formato de arquivo de montagem .NET](file-format.md)
- [Assemblies amigáveis](friend.md)
- [Assemblies de referência](reference-assemblies.md)
- [Como: Conjuntos de carga e descarga](load-unload.md)
- [Como: Usar e depurar a capacidade de descarga do conjunto no .NET Core](unloadability.md)
- [Como: Determinar se um arquivo é um conjunto](identify.md)
