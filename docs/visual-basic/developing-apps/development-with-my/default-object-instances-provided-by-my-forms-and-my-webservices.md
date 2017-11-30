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
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a><span data-ttu-id="3f6b1-102">Instâncias de objeto padrão fornecidas por My.Forms e My.WebServices (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f6b1-102">Default Object Instances Provided by My.Forms and My.WebServices (Visual Basic)</span></span>
<span data-ttu-id="3f6b1-103">O [My. Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) e [My. WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) objetos fornecem acesso a formulários, fontes de dados e serviços Web XML usados por seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3f6b1-103">The [My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) and [My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) objects provide access to forms, data sources, and XML Web services used by your application.</span></span> <span data-ttu-id="3f6b1-104">Eles fazem isso, fornecendo coleções de *instâncias padrão* de cada um desses objetos.</span><span class="sxs-lookup"><span data-stu-id="3f6b1-104">They do this by providing collections of *default instances* of each of these objects.</span></span>  
  
## <a name="default-instances"></a><span data-ttu-id="3f6b1-105">Instâncias padrão</span><span class="sxs-lookup"><span data-stu-id="3f6b1-105">Default Instances</span></span>  
 <span data-ttu-id="3f6b1-106">Uma instância padrão é uma instância da classe que é fornecida pelo tempo de execução e não precisa ser declarado e instanciado usando o `Dim` e `New` instruções.</span><span class="sxs-lookup"><span data-stu-id="3f6b1-106">A default instance is an instance of the class that is provided by the runtime and does not need to be declared and instantiated using the `Dim` and `New` statements.</span></span> <span data-ttu-id="3f6b1-107">O exemplo a seguir demonstra como você pode ter declarado e instanciado uma instância de um <xref:System.Windows.Forms.Form> classe chamada `Form1`, e como agora é possível obter uma instância padrão disso <xref:System.Windows.Forms.Form> classe por meio de `My.Forms`.</span><span class="sxs-lookup"><span data-stu-id="3f6b1-107">The following example demonstrates how you might have declared and instantiated an instance of a <xref:System.Windows.Forms.Form> class called `Form1`, and how you are now able to get a default instance of this <xref:System.Windows.Forms.Form> class through `My.Forms`.</span></span>  
  
 [!code-vb[VbVbcnMy#5](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_1.vb)]  
  
 [!code-vb[VbVbcnMy#6](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_2.vb)]  
  
 <span data-ttu-id="3f6b1-108">O `My.Forms` objeto retorna uma coleção de instâncias padrão para cada `Form` classe que existe em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="3f6b1-108">The `My.Forms` object returns a collection of default instances for every `Form` class that exists in your project.</span></span> <span data-ttu-id="3f6b1-109">Da mesma forma, `My.WebServices` fornece uma instância padrão da classe de proxy para cada serviço da Web que você criou uma referência para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3f6b1-109">Similarly, `My.WebServices` provides a default instance of the proxy class for every Web service that you have created a reference to in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f6b1-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f6b1-110">See Also</span></span>  
 [<span data-ttu-id="3f6b1-111">Objeto My.Forms</span><span class="sxs-lookup"><span data-stu-id="3f6b1-111">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)  
 [<span data-ttu-id="3f6b1-112">Objeto My.WebServices</span><span class="sxs-lookup"><span data-stu-id="3f6b1-112">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)  
 [<span data-ttu-id="3f6b1-113">Como My depende do tipo de projeto</span><span class="sxs-lookup"><span data-stu-id="3f6b1-113">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
