---
title: Instâncias de objeto padrão fornecidas por My.Forms e My.WebServices
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: d06df4bd023892429b2aaefdd624398a6546d06d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330213"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a>Instâncias de objeto padrão fornecidas por My.Forms e My.WebServices (Visual Basic)

Os objetos [My. Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) e [My. WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) fornecem acesso a formulários, fontes de dados e Web Services XML usados pelo seu aplicativo. Eles fazem isso fornecendo coleções de *instâncias padrão* de cada um desses objetos.  
  
## <a name="default-instances"></a>Instâncias padrão  

 Uma instância padrão é uma instância da classe fornecida pelo tempo de execução e não precisa ser declarada e instanciada usando as instruções `Dim` e `New`. O exemplo a seguir demonstra como você pode ter declarado e instanciado uma instância de uma classe <xref:System.Windows.Forms.Form> chamada `Form1`e como agora é possível obter uma instância padrão dessa classe <xref:System.Windows.Forms.Form> por meio de `My.Forms`.  
  
 [!code-vb[VbVbcnMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#5)]  
  
 [!code-vb[VbVbcnMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#6)]  
  
 O objeto `My.Forms` retorna uma coleção de instâncias padrão para cada classe `Form` que existe em seu projeto. Da mesma forma, `My.WebServices` fornece uma instância padrão da classe proxy para cada serviço Web ao qual você criou uma referência em seu aplicativo.  
  
## <a name="see-also"></a>Consulte também

- [Objeto My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [Objeto My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)
- [Como My depende do tipo de projeto](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
