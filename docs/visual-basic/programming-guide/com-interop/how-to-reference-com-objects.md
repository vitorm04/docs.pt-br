---
title: "Como fazer referência a objetos COM a partir do Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 694bd74e2b5ae374269accd845fe9178958bf56c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a>Como fazer referência a objetos COM a partir do Visual Basic
Em [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], adição de referências a objetos COM que têm bibliotecas de tipo exige a criação de um assembly de interoperabilidade para a biblioteca COM. Referências para os membros do objeto COM são roteadas para o assembly de interoperabilidade e, em seguida, encaminhadas para o objeto COM real. Respostas do objeto COM são roteadas para o assembly de interoperabilidade e encaminhadas para o seu [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplicativo.  
  
 Você pode fazer referência a um objeto COM sem usar um assembly de interoperabilidade, inserindo as informações do tipo do objeto COM em um assembly .NET. Para inserir informações de tipo, defina o `Embed Interop Types` propriedade `True` para a referência ao objeto COM. Se você estiver compilando usando o compilador de linha de comando, use o `/link` opção para fazer referência a biblioteca COM. Para obter mais informações, consulte [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]cria automaticamente os assemblies de interoperabilidade, quando você adiciona uma referência a uma biblioteca de tipos do ambiente de desenvolvimento integrado (IDE). Ao trabalhar na linha de comando, você pode usar o utilitário Tlbimp para criar manualmente os assemblies de interoperabilidade.  
  
### <a name="to-add-references-to-com-objects"></a>Para adicionar referências a objetos COM  
  
1.  Sobre o **projeto** menu, escolha **adicionar referência** e, em seguida, clique no **COM** guia na caixa de diálogo.  
  
2.  Selecione o componente que você deseja usar na lista de objetos COM.  
  
3.  Para simplificar o acesso ao assembly de interoperabilidade, adicione um `Imports` à parte superior da classe ou módulo que você irá usar o objeto COM. Por exemplo, o exemplo de código a seguir importa o namespace `INKEDLib` para objetos referenciados no `Microsoft InkEdit Control 1.0` biblioteca.  
  
     [!code-vb[VbVbalrInterop#40](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a>Para criar um assembly de interoperabilidade usando Tlbimp  
  
1.  Adicione o local do Tlbimp ao caminho de pesquisa, se ele não ainda faz parte do caminho de pesquisa e você não está no diretório onde ele está localizado.  
  
2.  Chame Tlbimp em um prompt de comando, fornecendo as seguintes informações:  
  
    -   Nome e o local da DLL que contém a biblioteca de tipos  
  
    -   Nome e localização do namespace onde as informações devem ser colocadas  
  
    -   Nome e local do assembly de interoperabilidade de destino  
  
     O código a seguir mostra um exemplo:  
  
    ```  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     Você pode usar Tlbimp para criar assemblies de interoperabilidade para bibliotecas de tipo, mesmo para objetos COM não registrados. No entanto, os objetos COM referenciado por assemblies de interoperabilidade devem ser registrados corretamente no computador onde eles devem ser usados. Você pode registrar um objeto COM usando o utilitário Regsvr32 incluído com o sistema operacional Windows.  
  
## <a name="see-also"></a>Consulte também  
 [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Tlbimp.exe (Importador de Biblioteca de Tipos)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)  
 [Tlbexp.exe (Exportador de Biblioteca de Tipos)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [Instruções passo a passo: implementando a herança com objetos COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [Solução de problemas de Interoperabilidade](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 [Instrução Imports (Tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
