---
title: 'Como: Referenciar objetos COM de Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
ms.openlocfilehash: 8e502dc9a279d9271a61fd2cf7a6afb564f09125
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351991"
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a>Como: Referenciar objetos COM de Visual Basic
No Visual Basic, a adição de referências a objetos COM que têm bibliotecas de tipos requer a criação de um assembly de interoperabilidade para a biblioteca COM. As referências aos membros do objeto COM são roteadas para o assembly de interoperabilidade e, em seguida, encaminhadas para o objeto COM real. As respostas do objeto COM são roteadas para o assembly de interoperabilidade e encaminhadas para seu aplicativo .NET Framework.  
  
 Você pode referenciar um objeto COM sem usar um assembly de interoperabilidade inserindo as informações de tipo para o objeto COM em um assembly .NET. Para inserir informações de tipo, defina a propriedade `Embed Interop Types` como `True` para a referência ao objeto COM. Se você estiver compilando usando o compilador de linha de comando, use a opção `/link` para fazer referência à biblioteca COM. Para obter mais informações, consulte [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).  
  
 Visual Basic cria automaticamente assemblies de interoperabilidade quando você adiciona uma referência a uma biblioteca de tipos do ambiente de desenvolvimento integrado (IDE). Ao trabalhar na linha de comando, você pode usar o utilitário TLBIMP para criar manualmente assemblies de interoperabilidade.  
  
### <a name="to-add-references-to-com-objects"></a>Para adicionar referências a objetos COM  
  
1. No menu **projeto** , escolha **Adicionar referência** e, em seguida, clique na guia **com** na caixa de diálogo.  
  
2. Selecione o componente que você deseja usar na lista de objetos COM.  
  
3. Para simplificar o acesso ao assembly de interoperabilidade, adicione uma instrução `Imports` à parte superior da classe ou do módulo no qual você usará o objeto COM. Por exemplo, o exemplo de código a seguir importa o namespace `INKEDLib` para objetos referenciados na biblioteca `Microsoft InkEdit Control 1.0`.  
  
     [!code-vb[VbVbalrInterop#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#40)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a>Para criar um assembly de interoperabilidade usando Tlbimp  
  
1. Adicione o local do Tlbimp ao caminho de pesquisa, se ele ainda não faz parte do caminho de pesquisa e você não está no diretório onde ele está localizado.  
  
2. Chame Tlbimp em um prompt de comando, fornecendo as seguintes informações:  
  
    - Nome e local da DLL que contém a biblioteca de tipos  
  
    - Nome e local do namespace onde as informações devem ser colocadas  
  
    - Nome e local do assembly de interoperabilidade de destino  
  
     O código a seguir mostra um exemplo:  
  
    ```console  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     Você pode usar Tlbimp para criar assemblies de interoperabilidade para bibliotecas de tipos, mesmo para objetos COM não registrados. No entanto, os objetos COM referenciados por assemblies de interoperabilidade devem ser registrados corretamente no computador onde eles devem ser usados. Você pode registrar um objeto COM usando o utilitário regsvr32 incluído no sistema operacional Windows.  
  
## <a name="see-also"></a>Consulte também

- [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md)
- [Tlbimp.exe (Importador de Biblioteca de Tipos)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (Exportador de Biblioteca de Tipos)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [Passo a passo: implementação de herança com objetos COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [Solução de problemas de Interoperabilidade](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
- [Instrução Imports (Tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
