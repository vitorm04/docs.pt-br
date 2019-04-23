---
title: Assemblies no .NET
ms.date: 07/10/2018
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
ms.openlocfilehash: 4a92eea623abc8aaad170dafc4bc3c917a36a474
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61627818"
---
# <a name="assemblies-in-net"></a>Assemblies no .NET

Os assemblies formam a unidade fundamental de implantação, controle de versão, reutilização, escopo de ativação e permissões de segurança para um aplicativo baseado em .NET Framework. Os assemblies tomam a forma de um arquivo executável (.exe) ou de biblioteca de link dinâmico (.dll) e são os blocos de construção dos aplicativos .NET. Eles oferecem ao Common Language Runtime as informações de que ele precisa para estar ciente das implementações de tipo. Você pode pensar em um assembly como uma coleção de tipos e recursos que formam uma unidade lógica de funcionalidade e são criados para trabalharem juntos.

No .NET Core e .NET Framework, um assembly pode ser criado em um ou mais arquivos de código-fonte. No .NET Framework, os assemblies podem conter um ou mais módulos. Isso permite que projetos maiores sejam planejados de forma que vários desenvolvedores individuais trabalhem em arquivos ou módulos de código-fonte separados, que são combinados para criar um único assembly. Para obter mais informações sobre os módulos, confira o tópico [Como: compilar um assembly de vários arquivos](../../framework/app-domains/how-to-build-a-multifile-assembly.md).

Os assemblies têm as seguintes propriedades:

- Assemblies são implementados como arquivos .dll ou .exe.

- Para bibliotecas destinadas ao .NET Framework, você pode compartilhar um assembly entre aplicativos colocando-o no [cache de assembly global](../../framework/app-domains/gac.md). Os assemblies devem ter nome forte antes de serem colocados no cache de assembly global. Para obter mais informações, consulte [Assemblies com nome forte](../../framework/app-domains/strong-named-assemblies.md).

- Os assemblies serão carregados na memória somente se forem necessários. Se não forem usados, eles não serão carregados. Isso significa que os assemblies podem ser uma maneira eficiente de gerenciar recursos em projetos grandes.

- Você pode obter informações programaticamente sobre um assembly usando reflexão. Para obter mais informações, confira [Reflexão (C#)](../../csharp/programming-guide/concepts/reflection.md) ou [Reflexão (Visual Basic)](../../visual-basic/programming-guide/concepts/reflection.md).

- Para carregar um assembly apenas para inspeção, chame um método <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType>.

## <a name="assembly-manifest"></a>Manifesto do assembly

Dentro de todo assembly está um *manifesto do assembly*. Semelhante a um sumário, o manifesto do assembly contém o seguinte:

- A identidade do assembly (seu nome e versão).

- Uma tabela de arquivos que descreve todos os outros arquivos que compõem o assembly, como outros assemblies que você criou dos quais seu arquivo .dll ou .exe depende, ou até arquivos bitmap ou Leiame.

- Uma *lista de referências de assembly*, que é uma lista de todas as dependências externas, .dlls ou outros arquivos que seu aplicativo precisa e que podem ter sido criados por outra pessoa. As referências de assembly contêm referências a objetos globais e privados. Os objetos globais estão disponíveis para todos os outros aplicativos. No .NET Core, eles são combinados com um determinado tempo de execução do .NET Core. No .NET Framework, eles residem no cache de assembly global. O namespace <xref:System.IO?displayProperty=nameWithType> é um exemplo de um assembly no cache de assembly global. Objetos privados devem estar em um diretório no mesmo nível ou abaixo do diretório no qual seu aplicativo está instalado.

Como os assemblies contêm informações sobre conteúdo, controle de versão e dependências, os aplicativos que os usam não precisam depender de valores do Registro do Windows para funcionar corretamente. Os assemblies reduzem conflitos de .dll e tornam seus aplicativos mais confiáveis e mais fáceis de implantar. Em muitos casos, você pode instalar um aplicativo baseado em .NET simplesmente copiando seus arquivos para o computador de destino. Para obter mais informações, confira [Manifesto do assembly](../../framework/app-domains/assembly-manifest.md).

## <a name="adding-a-reference-to-an-assembly"></a>Adicionar uma referência a um assembly

Para usar um assembly, você deve adicionar uma referência a ele. Em seguida, use a [diretiva using](../../csharp/language-reference/keywords/using-directive.md) para C# ou uma [instrução Imports](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para o Visual Basic para escolher o namespace dos itens que você deseja usar. Quando um assembly é referenciado e importado, todos os tipos, propriedades, métodos e outros membros acessíveis de seus namespaces são disponibilizados para seu aplicativo como se seus códigos fossem parte de seu arquivo de origem.

> [!NOTE]
> A maioria dos assemblies da Biblioteca de Classes .NET é referenciada automaticamente. Em alguns casos, no entanto, um assembly do sistema pode não ser referenciado automaticamente. No .NET Core, você pode adicionar uma referência ao pacote NuGet que contém o assembly usando o Gerenciador de Pacotes do NuGet no Visual Studio ou adicionando um elemento [\<PackageReference>](../../core/tools/dependencies.md#the-new-packagereference-element) do assembly ao projeto *.csproj ou *.vbproj. No .NET Framework, você pode adicionar uma referência ao assembly usando a caixa de diálogo **Adicionar referência** no Visual Studio ou usando a opção de linha de comando `-reference` para os compiladores do [C#](../../csharp/language-reference/compiler-options/reference-compiler-option.md) ou [Visual Basic](../../visual-basic/reference/command-line-compiler/reference.md).

No C#, você também pode usar duas versões do mesmo assembly em um único aplicativo. Para obter mais informações, consulte [alias externo](../../csharp/language-reference/keywords/extern-alias.md).

## <a name="creating-an-assembly"></a>Criar um assembly

Compile seu aplicativo criando-o no Visual Studio, criando-o a partir da linha de comando com as ferramentas de CLI (interface de linha de comando) do .NET Core ou criando os assemblies do .NET Framework com um compilador de linha de comando. Para obter mais informações sobre como compilar assemblies usando ferramentas de CLI do .NET, confira as [ferramentas de CLI (interface de linha de comando) do .NET Core](../../core/tools/index.md). Para compilar assemblies com os compiladores da linha de comando, confira [Compilar a linha de comando com csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) para C# e [Compilar da linha de comando](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) para Visual Basic.

> [!NOTE]
> Para criar um assembly no Visual Studio, no menu **Compilar**, escolha **Compilar**.

## <a name="see-also"></a>Consulte também

- [Formato de arquivo do assembly .NET](file-format.md)
- [Assemblies no Common Language Runtime](../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [Assemblies Amigáveis](friend-assemblies.md)
- [Como: carregar e descarregar assemblies (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-load-and-unload-assemblies.md)
- [Como: como carregar e descarregar assemblies (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-load-and-unload-assemblies.md)
- [Como: usar e depurar a Capacidade de descarregamento de assembly no .NET Core](unloadability-howto.md)
- [Como: determinar se um arquivo é um assembly (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-determine-if-a-file-is-an-assembly.md)
- [Como: determinar se um arquivo é um assembly (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-determine-if-a-file-is-an-assembly.md)
