---
title: Compilando um projeto de interoperabilidade
ms.date: 03/30/2017
helpviewer_keywords:
- interoperation with unmanaged code, compiling
- COM interop, compiling
- exposing COM components to .NET Framework
- compiling interop projects
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4369ce9c9ce82ecdbf11d76f3b043778b8374d8b
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489764"
---
# <a name="compiling-an-interop-project"></a>Compilando um projeto de interoperabilidade

Os projetos de interoperabilidade COM que referenciam um ou mais assemblies que contêm tipos COM importados são compilados como qualquer outro projeto gerenciado. É possível referenciar assemblies de interoperabilidade em um ambiente de desenvolvimento como o Visual Studio ou referenciá-los ao usar um compilador de linha de comando. Em ambos os casos, para ser compilado corretamente, o assembly de interoperabilidade deve estar no mesmo diretório dos outros arquivos de projeto.

 Há duas maneiras de referenciar assemblies de interoperabilidade:

- Tipos de interoperabilidade inseridos: Do .NET Framework 4 e do Visual Studio 2010 em diante, é possível instruir o compilador a inserir informações de tipo de um assembly de interoperabilidade ao seu executável. Esta é a técnica recomendada.

- Implantando assemblies de interoperabilidade: Crie uma referência padrão a um assembly de interoperabilidade. Nesse caso, o assembly de interoperabilidade deve ser implantado com o aplicativo.

 As diferenças entre essas duas técnicas são abordadas mais detalhadamente em [Usando tipos COM em um código gerenciado](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).

 A inserção de tipos de interoperabilidade com o Visual Studio é demonstrada em [Passo a passo: Inserindo tipos de assemblies gerenciados no Visual Studio (C#)](/docs/csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md) e [Passo a passo: Inserindo tipos de assemblies gerenciados no Visual Studio (Visual Basic)](/docs/visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md).

 Para referenciar um assembly de interoperabilidade com um compilador de linha de comando e inserir informações de tipo nos executáveis, use a opção do compilador [/link (Opções do Compilador do C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) ou [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) e especifique o nome do assembly de interoperabilidade.

> [!NOTE]
> Os aplicativos do Visual C++ não podem inserir informações de tipo, mas podem interoperar com aplicativos ou suplementos que têm essa capacidade.

 Para compilar um aplicativo que inclui um assembly de interoperabilidade primário quando ele é implantado, use a opção do compilador **/reference** e especifique o nome do assembly de interoperabilidade.

## <a name="see-also"></a>Consulte também

- [Expondo componentes do COM ao .NET Framework](exposing-com-components.md)
- [Componentes de independência de linguagem e componentes independentes da linguagem](../../standard/language-independence-and-language-independent-components.md)
- [Usando tipos COM no código gerenciado](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [Passo a passo: inserindo tipos de assemblies gerenciados no Visual Studio (C#)](/docs/csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)
- [Passo a passo: Inserindo tipos de assemblies gerenciados no Visual Studio (Visual Basic)](/docs/visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [Importando uma biblioteca de tipos como um assembly](importing-a-type-library-as-an-assembly.md)
