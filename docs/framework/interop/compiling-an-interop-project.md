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
ms.openlocfilehash: 7088c7f7765f0c5cfc4d6151dcda6f57b8de10d2
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086642"
---
# <a name="compiling-an-interop-project"></a>Compilando um projeto de interoperabilidade

Os projetos de interoperabilidade COM que referenciam um ou mais assemblies que contêm tipos COM importados são compilados como qualquer outro projeto gerenciado. É possível referenciar assemblies de interoperabilidade em um ambiente de desenvolvimento como o Visual Studio ou referenciá-los ao usar um compilador de linha de comando. Em ambos os casos, para ser compilado corretamente, o assembly de interoperabilidade deve estar no mesmo diretório dos outros arquivos de projeto.

 Há duas maneiras de referenciar assemblies de interoperabilidade:

-   Tipos de interoperabilidade inseridos: a partir do [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] e do Visual Studio 2010, é possível instruir o compilador a inserir informações de tipo de um assembly de interoperabilidade no executável. Esta é a técnica recomendada.

-   Implantando assemblies de interoperabilidade: é possível criar uma referência padrão a um assembly de interoperabilidade. Nesse caso, o assembly de interoperabilidade deve ser implantado com o aplicativo.

 As diferenças entre essas duas técnicas são abordadas mais detalhadamente em [Usando tipos COM em um código gerenciado](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100)).

 A inserção de tipos de interoperabilidade com o Visual Studio é demonstrada em [Passo a passo: Inserindo informações de tipos de assemblies do Microsoft Office](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100)) e [Passo a passo: Inserindo tipos de assemblies gerenciados](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).

 Para referenciar um assembly de interoperabilidade com um compilador de linha de comando e inserir informações de tipo nos executáveis, use a opção do compilador [/link (Opções do Compilador do C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) ou [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) e especifique o nome do assembly de interoperabilidade.

> [!NOTE]
> Os aplicativos do Visual C++ não podem inserir informações de tipo, mas podem interoperar com aplicativos ou suplementos que têm essa capacidade.

 Para compilar um aplicativo que inclui um assembly de interoperabilidade primário quando ele é implantado, use a opção do compilador **/reference** e especifique o nome do assembly de interoperabilidade.

## <a name="see-also"></a>Consulte também

- [Expondo componentes do COM ao .NET Framework](exposing-com-components.md)
- [Componentes de independência de linguagem e componentes independentes da linguagem](../../standard/language-independence-and-language-independent-components.md)
- [Usando tipos COM no código gerenciado](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))
- [Instruções passo a passo: inserindo informações de tipo dos Microsoft Office Assemblies](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))
- [Instruções passo a passo: inserindo tipos de assemblies gerenciados](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)
- [Importando uma biblioteca de tipos como um assembly](importing-a-type-library-as-an-assembly.md)