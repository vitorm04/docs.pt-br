---
title: O tipo '<typename>' não está definido
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: 3c22e6a5199bd52cb9fae66a15a66ac9ce095e81
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872201"
---
# <a name="type-typename-is-not-defined"></a><span data-ttu-id="d7bc7-102">O tipo '\<typename>' não está definido</span><span class="sxs-lookup"><span data-stu-id="d7bc7-102">Type '\<typename>' is not defined</span></span>

<span data-ttu-id="d7bc7-103">A instrução fez referência a um tipo que não foi definido.</span><span class="sxs-lookup"><span data-stu-id="d7bc7-103">The statement has made reference to a type that has not been defined.</span></span> <span data-ttu-id="d7bc7-104">Você pode definir um tipo em uma instrução de declaração, como `Enum` ,, `Structure` `Class` ou `Interface` .</span><span class="sxs-lookup"><span data-stu-id="d7bc7-104">You can define a type in a declaration statement such as `Enum`, `Structure`, `Class`, or `Interface`.</span></span>  
  
 <span data-ttu-id="d7bc7-105">**ID do erro:** BC30002</span><span class="sxs-lookup"><span data-stu-id="d7bc7-105">**Error ID:** BC30002</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d7bc7-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="d7bc7-106">To correct this error</span></span>  
  
- <span data-ttu-id="d7bc7-107">Verifique se a definição de tipo e sua referência usam a mesma grafia.</span><span class="sxs-lookup"><span data-stu-id="d7bc7-107">Ensure that the type definition and its reference both use the same spelling.</span></span>  
  
- <span data-ttu-id="d7bc7-108">Certifique-se de que a definição de tipo seja acessível para a referência.</span><span class="sxs-lookup"><span data-stu-id="d7bc7-108">Ensure that the type definition is accessible to the reference.</span></span> <span data-ttu-id="d7bc7-109">Por exemplo, se o tipo estiver em outro módulo e tiver sido declarado `Private` , mova a definição de tipo para o módulo de referência ou declare-a `Public` .</span><span class="sxs-lookup"><span data-stu-id="d7bc7-109">For example, if the type is in another module and has been declared `Private`, move the type definition to the referencing module or declare it `Public`.</span></span>  
  
- <span data-ttu-id="d7bc7-110">Certifique-se de que o namespace do tipo não seja redefinido no seu projeto.</span><span class="sxs-lookup"><span data-stu-id="d7bc7-110">Ensure that the namespace of the type is not redefined within your project.</span></span> <span data-ttu-id="d7bc7-111">Se for, use a `Global` palavra-chave para qualificar totalmente o nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="d7bc7-111">If it is, use the `Global` keyword to fully qualify the type name.</span></span> <span data-ttu-id="d7bc7-112">Por exemplo, se um projeto definir um namespace chamado `System` , o <xref:System.Object?displayProperty=nameWithType> tipo não poderá ser acessado, a menos que seja totalmente qualificado com a `Global` palavra-chave: `Global.System.Object` .</span><span class="sxs-lookup"><span data-stu-id="d7bc7-112">For example, if a project defines a namespace named `System`, the <xref:System.Object?displayProperty=nameWithType> type cannot be accessed unless it is fully qualified with the `Global` keyword: `Global.System.Object`.</span></span>  
  
- <span data-ttu-id="d7bc7-113">Se o tipo for definido, mas a biblioteca de objetos ou biblioteca de tipos na qual ele está definido não estiver registrada em Visual Basic, clique em **Adicionar referência** no menu **projeto** e selecione a biblioteca de objetos ou a biblioteca de tipos apropriada.</span><span class="sxs-lookup"><span data-stu-id="d7bc7-113">If the type is defined, but the object library or type library in which it is defined is not registered in Visual Basic, click **Add Reference** on the **Project** menu, and then select the appropriate object library or type library.</span></span>  
  
- <span data-ttu-id="d7bc7-114">Verifique se o tipo está em um assembly que faz parte do perfil de .NET Framework de destino.</span><span class="sxs-lookup"><span data-stu-id="d7bc7-114">Ensure that the type is in an assembly that is part of the targeted .NET Framework profile.</span></span> <span data-ttu-id="d7bc7-115">Para obter mais informações, consulte [Solução de problemas de erros de definição de destino do .NET Framework](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span><span class="sxs-lookup"><span data-stu-id="d7bc7-115">For more information, see [Troubleshooting .NET Framework Targeting Errors](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7bc7-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="d7bc7-116">See also</span></span>

- [<span data-ttu-id="d7bc7-117">Namespaces no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d7bc7-117">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="d7bc7-118">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="d7bc7-118">Enum Statement</span></span>](../statements/enum-statement.md)
- [<span data-ttu-id="d7bc7-119">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="d7bc7-119">Structure Statement</span></span>](../statements/structure-statement.md)
- [<span data-ttu-id="d7bc7-120">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="d7bc7-120">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="d7bc7-121">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="d7bc7-121">Interface Statement</span></span>](../statements/interface-statement.md)
- [<span data-ttu-id="d7bc7-122">Gerenciando referências em um projeto</span><span class="sxs-lookup"><span data-stu-id="d7bc7-122">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
