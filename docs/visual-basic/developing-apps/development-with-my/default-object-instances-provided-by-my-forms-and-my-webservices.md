---
title: "Instâncias de objeto padrão fornecidas por My.Forms e My.WebServices (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 44265c3f6f38a001192a8d92f2fbb6edeaca21cb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a>Instâncias de objeto padrão fornecidas por My.Forms e My.WebServices (Visual Basic)
O [My. Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) e [My. WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) objetos fornecem acesso a formulários, fontes de dados e serviços Web XML usados por seu aplicativo. Eles fazem isso, fornecendo coleções de *instâncias padrão* de cada um desses objetos.  
  
## <a name="default-instances"></a>Instâncias padrão  
 Uma instância padrão é uma instância da classe que é fornecida pelo tempo de execução e não precisa ser declarado e instanciado usando o `Dim` e `New` instruções. O exemplo a seguir demonstra como você pode ter declarado e instanciado uma instância de um <xref:System.Windows.Forms.Form> classe chamada `Form1`, e como agora é possível obter uma instância padrão disso <xref:System.Windows.Forms.Form> classe por meio de `My.Forms`.  
  
 [!code-vb[VbVbcnMy#5](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_1.vb)]  
  
 [!code-vb[VbVbcnMy#6](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_2.vb)]  
  
 O `My.Forms` objeto retorna uma coleção de instâncias padrão para cada `Form` classe que existe em seu projeto. Da mesma forma, `My.WebServices` fornece uma instância padrão da classe de proxy para cada serviço da Web que você criou uma referência para seu aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Objeto My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)  
 [Objeto My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)  
 [Como My depende do tipo de projeto](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
