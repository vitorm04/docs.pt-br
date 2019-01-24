---
title: Instâncias de objeto padrão fornecidas por My.Forms e My.WebServices (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: 9285e88e3dc9fd8b3731416b1c40811188d6a33d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563594"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a><span data-ttu-id="a319e-102">Instâncias de objeto padrão fornecidas por My.Forms e My.WebServices (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a319e-102">Default Object Instances Provided by My.Forms and My.WebServices (Visual Basic)</span></span>
<span data-ttu-id="a319e-103">O [My. Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) e [My. WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) objetos fornecem acesso a formulários, fontes de dados e serviços Web XML usados por seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a319e-103">The [My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) and [My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) objects provide access to forms, data sources, and XML Web services used by your application.</span></span> <span data-ttu-id="a319e-104">Eles fazem isso, fornecendo coleções de *instâncias padrão* de cada um desses objetos.</span><span class="sxs-lookup"><span data-stu-id="a319e-104">They do this by providing collections of *default instances* of each of these objects.</span></span>  
  
## <a name="default-instances"></a><span data-ttu-id="a319e-105">Instâncias padrão</span><span class="sxs-lookup"><span data-stu-id="a319e-105">Default Instances</span></span>  
 <span data-ttu-id="a319e-106">Uma instância padrão é uma instância da classe que é fornecida pelo tempo de execução e não precisa ser declarado e instanciado usando o `Dim` e `New` instruções.</span><span class="sxs-lookup"><span data-stu-id="a319e-106">A default instance is an instance of the class that is provided by the runtime and does not need to be declared and instantiated using the `Dim` and `New` statements.</span></span> <span data-ttu-id="a319e-107">O exemplo a seguir demonstra como você pode ter declarado e instanciado uma instância de um <xref:System.Windows.Forms.Form> classe chamada `Form1`, e como você agora pode obter uma instância padrão disso <xref:System.Windows.Forms.Form> por meio de classe `My.Forms`.</span><span class="sxs-lookup"><span data-stu-id="a319e-107">The following example demonstrates how you might have declared and instantiated an instance of a <xref:System.Windows.Forms.Form> class called `Form1`, and how you are now able to get a default instance of this <xref:System.Windows.Forms.Form> class through `My.Forms`.</span></span>  
  
 [!code-vb[VbVbcnMy#5](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_1.vb)]  
  
 [!code-vb[VbVbcnMy#6](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/default-object-instances-provided-by-my-forms-and-my-webservices_2.vb)]  
  
 <span data-ttu-id="a319e-108">O `My.Forms` objeto retorna uma coleção de instâncias padrão para cada `Form` classe existe em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="a319e-108">The `My.Forms` object returns a collection of default instances for every `Form` class that exists in your project.</span></span> <span data-ttu-id="a319e-109">Da mesma forma, `My.WebServices` fornece uma instância padrão da classe de proxy para cada serviço da Web que você criou uma referência ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a319e-109">Similarly, `My.WebServices` provides a default instance of the proxy class for every Web service that you have created a reference to in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a319e-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a319e-110">See also</span></span>
- [<span data-ttu-id="a319e-111">Objeto My.Forms</span><span class="sxs-lookup"><span data-stu-id="a319e-111">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [<span data-ttu-id="a319e-112">Objeto My.WebServices</span><span class="sxs-lookup"><span data-stu-id="a319e-112">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)
- [<span data-ttu-id="a319e-113">Como My depende do tipo de projeto</span><span class="sxs-lookup"><span data-stu-id="a319e-113">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
