---
title: "Padrão de instâncias de objeto fornecidas pelo My. Forms e My. WebServices (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- My.WebServices object, developing applications
- My.Forms object, developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
caps.latest.revision: 5
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 193f3a87b9ae6a46554cb01212070a4441496627
ms.lasthandoff: 03/13/2017

---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a>Instâncias de objeto padrão fornecidas por My.Forms e My.WebServices (Visual Basic)
O [My. Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) e [My. WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) objetos fornecem acesso a formulários, fontes de dados e serviços Web XML usados por seu aplicativo. Eles fazem isso, fornecendo coleções de *instâncias padrão* de cada um desses objetos.  
  
## <a name="default-instances"></a>Instâncias padrão  
 Uma instância padrão é uma instância da classe que é fornecida pelo tempo de execução e não precisa ser declarada e instanciada usando o `Dim` e `New` instruções. O exemplo a seguir demonstra como você pode ter declarado e instanciado uma instância de um <xref:System.Windows.Forms.Form>classe chamada `Form1`, e como você agora pode obter uma instância padrão desta <xref:System.Windows.Forms.Form>por meio da classe `My.Forms`.</xref:System.Windows.Forms.Form> </xref:System.Windows.Forms.Form>  
  
 [!code-vb[VbVbcnMy n º&5;](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_1.vb)]  
  
 [!code-vb[VbVbcnMy n º&6;](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_2.vb)]  
  
 O `My.Forms` objeto retorna uma coleção de instâncias padrão para cada `Form` classe que existe em seu projeto. Da mesma forma, `My.WebServices` fornece uma instância padrão da classe de proxy para cada serviço da Web que você criou uma referência para seu aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Objeto My. Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)   
 [Objeto My. WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)   
 [Como My depende do tipo de projeto](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
