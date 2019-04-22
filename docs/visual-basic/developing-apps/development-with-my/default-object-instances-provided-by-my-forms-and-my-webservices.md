---
title: Instâncias de objeto padrão fornecidas por My.Forms e My.WebServices (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: ca31e1c40c77bf7f42d246019d81f4ffaed646e8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839351"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a>Instâncias de objeto padrão fornecidas por My.Forms e My.WebServices (Visual Basic)
O [My. Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) e [My. WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) objetos fornecem acesso a formulários, fontes de dados e serviços Web XML usados por seu aplicativo. Eles fazem isso, fornecendo coleções de *instâncias padrão* de cada um desses objetos.  
  
## <a name="default-instances"></a>Instâncias padrão  
 Uma instância padrão é uma instância da classe que é fornecida pelo tempo de execução e não precisa ser declarado e instanciado usando o `Dim` e `New` instruções. O exemplo a seguir demonstra como você pode ter declarado e instanciado uma instância de um <xref:System.Windows.Forms.Form> classe chamada `Form1`, e como você agora pode obter uma instância padrão disso <xref:System.Windows.Forms.Form> por meio de classe `My.Forms`.  
  
 [!code-vb[VbVbcnMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#5)]  
  
 [!code-vb[VbVbcnMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#6)]  
  
 O `My.Forms` objeto retorna uma coleção de instâncias padrão para cada `Form` classe existe em seu projeto. Da mesma forma, `My.WebServices` fornece uma instância padrão da classe de proxy para cada serviço da Web que você criou uma referência ao seu aplicativo.  
  
## <a name="see-also"></a>Consulte também

- [Objeto My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [Objeto My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)
- [Como My depende do tipo de projeto](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
