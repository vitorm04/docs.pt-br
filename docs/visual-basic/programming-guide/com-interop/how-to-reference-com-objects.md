---
title: Como fazer referência a objetos COM a partir do Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
ms.openlocfilehash: 293bf76b1520f50e67837942eab2f27a49e330e3
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44204780"
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a>Como fazer referência a objetos COM a partir do Visual Basic
No Visual Basic, a adição de referências a objetos COM que têm bibliotecas de tipo requer a criação de um assembly de interoperabilidade para a biblioteca COM. As referências aos membros do objeto COM são roteadas para o assembly de interoperabilidade e, em seguida, encaminhadas para o objeto COM real. As respostas do objeto COM são roteadas para o assembly de interoperabilidade e encaminhadas para seu [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplicativo.  
  
 Você pode fazer referência a um objeto COM sem o uso de um assembly de interoperabilidade, incorporando as informações de tipo para o objeto COM em um assembly .NET. Para inserir informações de tipo, defina as `Embed Interop Types` propriedade para `True` para a referência ao objeto COM. Se você estiver compilando usando o compilador de linha de comando, use o `/link` opção para fazer referência a biblioteca COM. Para obter mais informações, consulte [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).  
  
 Visual Basic cria automaticamente os assemblies de interoperabilidade quando você adiciona uma referência a uma biblioteca de tipos de ambiente de desenvolvimento integrado (IDE). Ao trabalhar na linha de comando, você pode usar o utilitário Tlbimp para criar manualmente os assemblies de interoperabilidade.  
  
### <a name="to-add-references-to-com-objects"></a>Para adicionar referências a objetos COM  
  
1.  Sobre o **projeto** menu, escolha **adicionar referência** e, em seguida, clique no **COM** guia na caixa de diálogo.  
  
2.  Selecione o componente que você deseja usar na lista de objetos COM.  
  
3.  Para simplificar o acesso ao assembly de interoperabilidade, adicione um `Imports` instrução na parte superior da classe ou módulo que você usará o objeto COM. Por exemplo, o exemplo de código a seguir importa o namespace `INKEDLib` para objetos referenciados no `Microsoft InkEdit Control 1.0` biblioteca.  
  
     [!code-vb[VbVbalrInterop#40](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a>Para criar um assembly de interoperabilidade usando Tlbimp  
  
1.  Adicione o local do Tlbimp ao caminho de pesquisa, se ele não ainda faz parte do caminho de pesquisa e você não estiver atualmente no diretório onde ele está localizado.  
  
2.  Tlbimp chamada em um prompt de comando, fornecendo as seguintes informações:  
  
    -   Nome e o local da DLL que contém a biblioteca de tipos  
  
    -   Nome e o local do namespace onde as informações devem ser colocadas  
  
    -   Nome e local do assembly de interoperabilidade de destino  
  
     O código a seguir mostra um exemplo:  
  
    ```  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     Você pode usar Tlbimp para criar assemblies de interoperabilidade para bibliotecas de tipos, mesmo para objetos COM não registrados. No entanto, os objetos COM referenciados por assemblies de interoperabilidade devem ser registrados corretamente no computador em que eles devem ser usados. Você pode registrar um objeto COM por meio do utilitário Regsvr32 incluído com o sistema operacional Windows.  
  
## <a name="see-also"></a>Consulte também

- [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md)  
- [Tlbimp.exe (Importador de Biblioteca de Tipos)](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
- [Tlbexp.exe (Exportador de Biblioteca de Tipos)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)  
- [Instruções passo a passo: implementando a herança com objetos COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
- [Solução de problemas de Interoperabilidade](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
- [Instrução Imports (Tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
