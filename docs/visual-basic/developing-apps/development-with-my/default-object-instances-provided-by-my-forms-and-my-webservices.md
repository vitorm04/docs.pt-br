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
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a><span data-ttu-id="bd409-102">Instâncias de objeto padrão fornecidas por My.Forms e My.WebServices (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd409-102">Default Object Instances Provided by My.Forms and My.WebServices (Visual Basic)</span></span>

<span data-ttu-id="bd409-103">Os objetos [My. Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) e [My. WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) fornecem acesso a formulários, fontes de dados e Web Services XML usados pelo seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bd409-103">The [My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) and [My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) objects provide access to forms, data sources, and XML Web services used by your application.</span></span> <span data-ttu-id="bd409-104">Eles fazem isso fornecendo coleções de *instâncias padrão* de cada um desses objetos.</span><span class="sxs-lookup"><span data-stu-id="bd409-104">They do this by providing collections of *default instances* of each of these objects.</span></span>  
  
## <a name="default-instances"></a><span data-ttu-id="bd409-105">Instâncias padrão</span><span class="sxs-lookup"><span data-stu-id="bd409-105">Default Instances</span></span>  

 <span data-ttu-id="bd409-106">Uma instância padrão é uma instância da classe fornecida pelo tempo de execução e não precisa ser declarada e instanciada usando as instruções `Dim` e `New`.</span><span class="sxs-lookup"><span data-stu-id="bd409-106">A default instance is an instance of the class that is provided by the runtime and does not need to be declared and instantiated using the `Dim` and `New` statements.</span></span> <span data-ttu-id="bd409-107">O exemplo a seguir demonstra como você pode ter declarado e instanciado uma instância de uma classe <xref:System.Windows.Forms.Form> chamada `Form1`e como agora é possível obter uma instância padrão dessa classe <xref:System.Windows.Forms.Form> por meio de `My.Forms`.</span><span class="sxs-lookup"><span data-stu-id="bd409-107">The following example demonstrates how you might have declared and instantiated an instance of a <xref:System.Windows.Forms.Form> class called `Form1`, and how you are now able to get a default instance of this <xref:System.Windows.Forms.Form> class through `My.Forms`.</span></span>  
  
 [!code-vb[VbVbcnMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#5)]  
  
 [!code-vb[VbVbcnMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#6)]  
  
 <span data-ttu-id="bd409-108">O objeto `My.Forms` retorna uma coleção de instâncias padrão para cada classe `Form` que existe em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="bd409-108">The `My.Forms` object returns a collection of default instances for every `Form` class that exists in your project.</span></span> <span data-ttu-id="bd409-109">Da mesma forma, `My.WebServices` fornece uma instância padrão da classe proxy para cada serviço Web ao qual você criou uma referência em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bd409-109">Similarly, `My.WebServices` provides a default instance of the proxy class for every Web service that you have created a reference to in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd409-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd409-110">See also</span></span>

- [<span data-ttu-id="bd409-111">Objeto My.Forms</span><span class="sxs-lookup"><span data-stu-id="bd409-111">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [<span data-ttu-id="bd409-112">Objeto My.WebServices</span><span class="sxs-lookup"><span data-stu-id="bd409-112">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)
- [<span data-ttu-id="bd409-113">Como My depende do tipo de projeto</span><span class="sxs-lookup"><span data-stu-id="bd409-113">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
