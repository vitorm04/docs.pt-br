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
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ae99398d17ec7f57b04ff156e6e2842e43e1829c
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a><span data-ttu-id="bd6b6-102">Instâncias de objeto padrão fornecidas por My.Forms e My.WebServices (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd6b6-102">Default Object Instances Provided by My.Forms and My.WebServices (Visual Basic)</span></span>
<span data-ttu-id="bd6b6-103">O [My. Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) e [My. WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) objetos fornecem acesso a formulários, fontes de dados e serviços Web XML usados por seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bd6b6-103">The [My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) and [My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) objects provide access to forms, data sources, and XML Web services used by your application.</span></span> <span data-ttu-id="bd6b6-104">Eles fazem isso, fornecendo coleções de *instâncias padrão* de cada um desses objetos.</span><span class="sxs-lookup"><span data-stu-id="bd6b6-104">They do this by providing collections of *default instances* of each of these objects.</span></span>  
  
## <a name="default-instances"></a><span data-ttu-id="bd6b6-105">Instâncias padrão</span><span class="sxs-lookup"><span data-stu-id="bd6b6-105">Default Instances</span></span>  
 <span data-ttu-id="bd6b6-106">Uma instância padrão é uma instância da classe que é fornecida pelo tempo de execução e não precisa ser declarada e instanciada usando o `Dim` e `New` instruções.</span><span class="sxs-lookup"><span data-stu-id="bd6b6-106">A default instance is an instance of the class that is provided by the runtime and does not need to be declared and instantiated using the `Dim` and `New` statements.</span></span> <span data-ttu-id="bd6b6-107">O exemplo a seguir demonstra como você pode ter declarado e instanciado uma instância de um <xref:System.Windows.Forms.Form>classe chamada `Form1`, e como você agora pode obter uma instância padrão desta <xref:System.Windows.Forms.Form>por meio da classe `My.Forms`.</xref:System.Windows.Forms.Form> </xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="bd6b6-107">The following example demonstrates how you might have declared and instantiated an instance of a <xref:System.Windows.Forms.Form> class called `Form1`, and how you are now able to get a default instance of this <xref:System.Windows.Forms.Form> class through `My.Forms`.</span></span>  
  
 <span data-ttu-id="bd6b6-108">[!code-vb[VbVbcnMy n º&5;](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="bd6b6-108">[!code-vb[VbVbcnMy#5](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_1.vb)]</span></span>  
  
 <span data-ttu-id="bd6b6-109">[!code-vb[VbVbcnMy n º&6;](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="bd6b6-109">[!code-vb[VbVbcnMy#6](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_2.vb)]</span></span>  
  
 <span data-ttu-id="bd6b6-110">O `My.Forms` objeto retorna uma coleção de instâncias padrão para cada `Form` classe que existe em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="bd6b6-110">The `My.Forms` object returns a collection of default instances for every `Form` class that exists in your project.</span></span> <span data-ttu-id="bd6b6-111">Da mesma forma, `My.WebServices` fornece uma instância padrão da classe de proxy para cada serviço da Web que você criou uma referência para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bd6b6-111">Similarly, `My.WebServices` provides a default instance of the proxy class for every Web service that you have created a reference to in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd6b6-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd6b6-112">See Also</span></span>  
 <span data-ttu-id="bd6b6-113">[Objeto My. Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) </span><span class="sxs-lookup"><span data-stu-id="bd6b6-113">[My.Forms Object](../../../visual-basic/language-reference/objects/my-forms-object.md) </span></span>  
<span data-ttu-id="bd6b6-114"> [Objeto My. WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) </span><span class="sxs-lookup"><span data-stu-id="bd6b6-114"> [My.WebServices Object](../../../visual-basic/language-reference/objects/my-webservices-object.md) </span></span>  
<span data-ttu-id="bd6b6-115"> [Como My depende do tipo de projeto](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)</span><span class="sxs-lookup"><span data-stu-id="bd6b6-115"> [How My Depends on Project Type](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)</span></span>
