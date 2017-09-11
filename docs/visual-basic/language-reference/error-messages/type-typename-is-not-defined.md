---
title: "Tipo de &quot;&lt;typename&gt;&quot; não está definido | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30002
- bc30002
dev_langs:
- VB
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
caps.latest.revision: 18
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
ms.openlocfilehash: 55b76e9d080a2e2e9fe6e9737a713524ea6409f6
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="type-39lttypenamegt39-is-not-defined"></a><span data-ttu-id="54d39-102">Tipo de '&lt;typename&gt;' não está definido</span><span class="sxs-lookup"><span data-stu-id="54d39-102">Type &#39;&lt;typename&gt;&#39; is not defined</span></span>
<span data-ttu-id="54d39-103">A instrução faz referência a um tipo que não foi definida.</span><span class="sxs-lookup"><span data-stu-id="54d39-103">The statement has made reference to a type that has not been defined.</span></span> <span data-ttu-id="54d39-104">Você pode definir um tipo em uma instrução de declaração, como `Enum`, `Structure`, `Class`, ou `Interface`.</span><span class="sxs-lookup"><span data-stu-id="54d39-104">You can define a type in a declaration statement such as `Enum`, `Structure`, `Class`, or `Interface`.</span></span>  
  
 <span data-ttu-id="54d39-105">**ID do erro:** BC30002</span><span class="sxs-lookup"><span data-stu-id="54d39-105">**Error ID:** BC30002</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="54d39-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="54d39-106">To correct this error</span></span>  
  
-   <span data-ttu-id="54d39-107">Certifique-se de que a definição de tipo e sua referência usam a mesma ortografia.</span><span class="sxs-lookup"><span data-stu-id="54d39-107">Ensure that the type definition and its reference both use the same spelling.</span></span>  
  
-   <span data-ttu-id="54d39-108">Certifique-se de que a definição de tipo é acessível para a referência.</span><span class="sxs-lookup"><span data-stu-id="54d39-108">Ensure that the type definition is accessible to the reference.</span></span> <span data-ttu-id="54d39-109">Por exemplo, se o tipo estiver em outro módulo e foi declarado `Private`, mover a definição de tipo para o módulo de referência ou declare- `Public`.</span><span class="sxs-lookup"><span data-stu-id="54d39-109">For example, if the type is in another module and has been declared `Private`, move the type definition to the referencing module or declare it `Public`.</span></span>  
  
-   <span data-ttu-id="54d39-110">Certifique-se de que o namespace do tipo não é redefinido no seu projeto.</span><span class="sxs-lookup"><span data-stu-id="54d39-110">Ensure that the namespace of the type is not redefined within your project.</span></span> <span data-ttu-id="54d39-111">Se for, use o `Global` palavra-chave para qualificar totalmente o nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="54d39-111">If it is, use the `Global` keyword to fully qualify the type name.</span></span> <span data-ttu-id="54d39-112">Por exemplo, se um projeto define um namespace chamado `System`, o <xref:System.Object?displayProperty=fullName>tipo não pode ser acessado, a menos que ele seja totalmente qualificado com o `Global` palavra-chave: `Global.System.Object`.</xref:System.Object?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="54d39-112">For example, if a project defines a namespace named `System`, the <xref:System.Object?displayProperty=fullName> type cannot be accessed unless it is fully qualified with the `Global` keyword: `Global.System.Object`.</span></span>  
  
-   <span data-ttu-id="54d39-113">Se o tipo é definido, mas a biblioteca de objeto ou no qual ele é definido de biblioteca de tipos não está registrada no [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], clique em **adicionar referência** sobre o **projeto** menu e, em seguida, selecione a biblioteca de objeto apropriado ou biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="54d39-113">If the type is defined, but the object library or type library in which it is defined is not registered in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], click **Add Reference** on the **Project** menu, and then select the appropriate object library or type library.</span></span>  
  
-   <span data-ttu-id="54d39-114">Certifique-se de que o tipo é em um assembly que é parte do perfil de destino do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="54d39-114">Ensure that the type is in an assembly that is part of the targeted .NET Framework profile.</span></span> <span data-ttu-id="54d39-115">Para obter mais informações, consulte [de solução de problemas de direcionamento erros do .NET Framework](https://docs.microsoft.com/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span><span class="sxs-lookup"><span data-stu-id="54d39-115">For more information, see [Troubleshooting .NET Framework Targeting Errors](https://docs.microsoft.com/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54d39-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54d39-116">See Also</span></span>  
 <span data-ttu-id="54d39-117">[Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span><span class="sxs-lookup"><span data-stu-id="54d39-117">[Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span></span>  
<span data-ttu-id="54d39-118"> [Instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md) </span><span class="sxs-lookup"><span data-stu-id="54d39-118"> [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md) </span></span>  
<span data-ttu-id="54d39-119"> [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md) </span><span class="sxs-lookup"><span data-stu-id="54d39-119"> [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) </span></span>  
<span data-ttu-id="54d39-120"> [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md) </span><span class="sxs-lookup"><span data-stu-id="54d39-120"> [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) </span></span>  
<span data-ttu-id="54d39-121"> [Instrução interface](../../../visual-basic/language-reference/statements/interface-statement.md) </span><span class="sxs-lookup"><span data-stu-id="54d39-121"> [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) </span></span>  
<span data-ttu-id="54d39-122"> [Gerenciando referências em um projeto](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)</span><span class="sxs-lookup"><span data-stu-id="54d39-122"> [Managing references in a project](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)</span></span>
