---
title: Tipo &#39; &lt;typename&gt; &#39; não está definido
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: 20f36a06000d0197ad80b83766f6612a474d5758
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595180"
---
# <a name="type-39lttypenamegt39-is-not-defined"></a><span data-ttu-id="1827d-102">Tipo &#39; &lt;typename&gt; &#39; não está definido</span><span class="sxs-lookup"><span data-stu-id="1827d-102">Type &#39;&lt;typename&gt;&#39; is not defined</span></span>
<span data-ttu-id="1827d-103">A instrução faz referência a um tipo que não foi definida.</span><span class="sxs-lookup"><span data-stu-id="1827d-103">The statement has made reference to a type that has not been defined.</span></span> <span data-ttu-id="1827d-104">Você pode definir um tipo em uma instrução de declaração, como `Enum`, `Structure`, `Class`, ou `Interface`.</span><span class="sxs-lookup"><span data-stu-id="1827d-104">You can define a type in a declaration statement such as `Enum`, `Structure`, `Class`, or `Interface`.</span></span>  
  
 <span data-ttu-id="1827d-105">**ID do erro:** BC30002</span><span class="sxs-lookup"><span data-stu-id="1827d-105">**Error ID:** BC30002</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1827d-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="1827d-106">To correct this error</span></span>  
  
-   <span data-ttu-id="1827d-107">Certifique-se de que a definição de tipo e sua referência ambos usam a mesma ortografia.</span><span class="sxs-lookup"><span data-stu-id="1827d-107">Ensure that the type definition and its reference both use the same spelling.</span></span>  
  
-   <span data-ttu-id="1827d-108">Certifique-se de que a definição de tipo é acessível para a referência.</span><span class="sxs-lookup"><span data-stu-id="1827d-108">Ensure that the type definition is accessible to the reference.</span></span> <span data-ttu-id="1827d-109">Por exemplo, se o tipo é em outro módulo e foi declarado `Private`, mover a definição de tipo para o módulo de referência ou declare- `Public`.</span><span class="sxs-lookup"><span data-stu-id="1827d-109">For example, if the type is in another module and has been declared `Private`, move the type definition to the referencing module or declare it `Public`.</span></span>  
  
-   <span data-ttu-id="1827d-110">Certifique-se de que o namespace do tipo não é referenciado dentro de seu projeto.</span><span class="sxs-lookup"><span data-stu-id="1827d-110">Ensure that the namespace of the type is not redefined within your project.</span></span> <span data-ttu-id="1827d-111">Se for, use o `Global` palavra-chave para qualificar totalmente o nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="1827d-111">If it is, use the `Global` keyword to fully qualify the type name.</span></span> <span data-ttu-id="1827d-112">Por exemplo, se um projeto define um namespace chamado `System`, o <xref:System.Object?displayProperty=nameWithType> tipo não pode ser acessado, a menos que ele seja totalmente qualificado com o `Global` palavra-chave: `Global.System.Object`.</span><span class="sxs-lookup"><span data-stu-id="1827d-112">For example, if a project defines a namespace named `System`, the <xref:System.Object?displayProperty=nameWithType> type cannot be accessed unless it is fully qualified with the `Global` keyword: `Global.System.Object`.</span></span>  
  
-   <span data-ttu-id="1827d-113">Se o tipo é definido, mas a biblioteca de objeto ou a biblioteca de tipo no qual ele é definido não está registrada no Visual Basic, clique em **adicionar referência** no **projeto** menu e, em seguida, selecione o objeto apropriado biblioteca ou biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="1827d-113">If the type is defined, but the object library or type library in which it is defined is not registered in Visual Basic, click **Add Reference** on the **Project** menu, and then select the appropriate object library or type library.</span></span>  
  
-   <span data-ttu-id="1827d-114">Certifique-se de que o tipo é em um assembly que é parte do perfil do .NET Framework de destino.</span><span class="sxs-lookup"><span data-stu-id="1827d-114">Ensure that the type is in an assembly that is part of the targeted .NET Framework profile.</span></span> <span data-ttu-id="1827d-115">Para obter mais informações, consulte [Solução de problemas de erros de definição de destino do .NET Framework](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span><span class="sxs-lookup"><span data-stu-id="1827d-115">For more information, see [Troubleshooting .NET Framework Targeting Errors](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1827d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1827d-116">See Also</span></span>  
 [<span data-ttu-id="1827d-117">Namespaces no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1827d-117">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="1827d-118">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="1827d-118">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="1827d-119">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="1827d-119">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="1827d-120">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="1827d-120">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="1827d-121">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="1827d-121">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="1827d-122">Gerenciando referências em um projeto</span><span class="sxs-lookup"><span data-stu-id="1827d-122">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
