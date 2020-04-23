---
title: Como compartilhar um assembly com outros aplicativos
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: b4c183c3fc0b04121be8bbc2db4027887cbc3132
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644285"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a><span data-ttu-id="58997-102">Como compartilhar um assembly com outros aplicativos</span><span class="sxs-lookup"><span data-stu-id="58997-102">How to: Share an assembly with other applications</span></span>
<span data-ttu-id="58997-103">Os assemblies podem ser particulares ou compartilhados: por padrão, a maioria dos programas simples consistem em um assembly particular porque eles não se destinam a serem usados por outros aplicativos.</span><span class="sxs-lookup"><span data-stu-id="58997-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  

<span data-ttu-id="58997-104">Para compartilhar um assembly com outros aplicativos, ele deve ser colocado no [GAC (cache de assembly global)](gac.md).</span><span class="sxs-lookup"><span data-stu-id="58997-104">In order to share an assembly with other applications, it must be placed in the [global assembly cache (GAC)](gac.md).</span></span>  
  
<span data-ttu-id="58997-105">Para compartilhar um assembly:</span><span class="sxs-lookup"><span data-stu-id="58997-105">To share an assembly:</span></span>
  
1. <span data-ttu-id="58997-106">Crie o assembly.</span><span class="sxs-lookup"><span data-stu-id="58997-106">Create your assembly.</span></span> <span data-ttu-id="58997-107">Para obter mais informações, consulte [criar assemblies](../../standard/assembly/create.md).</span><span class="sxs-lookup"><span data-stu-id="58997-107">For more information, see [Create assemblies](../../standard/assembly/create.md).</span></span>  
  
2. <span data-ttu-id="58997-108">Atribua um nome forte ao assembly.</span><span class="sxs-lookup"><span data-stu-id="58997-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="58997-109">Para obter mais informações, consulte [como assinar um assembly com um nome forte](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="58997-109">For more information, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>  
  
3. <span data-ttu-id="58997-110">Atribua informações de versão ao assembly.</span><span class="sxs-lookup"><span data-stu-id="58997-110">Assign version information to your assembly.</span></span> <span data-ttu-id="58997-111">Para obter mais informações, consulte [controle de versão do assembly](../../standard/assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="58997-111">For more information, see [Assembly versioning](../../standard/assembly/versioning.md).</span></span>  
  
4. <span data-ttu-id="58997-112">Adicione seu assembly ao cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="58997-112">Add your assembly to the global assembly cache.</span></span> <span data-ttu-id="58997-113">Para obter mais informações, consulte [como: instalar um assembly no cache de assembly global](install-assembly-into-gac.md).</span><span class="sxs-lookup"><span data-stu-id="58997-113">For more information, see [How to: Install an assembly into the global assembly cache](install-assembly-into-gac.md).</span></span>  
  
5. <span data-ttu-id="58997-114">Acesse os tipos contidos no assembly de outros aplicativos.</span><span class="sxs-lookup"><span data-stu-id="58997-114">Access the types contained in the assembly from other applications.</span></span> <span data-ttu-id="58997-115">Para obter mais informações, consulte [como referenciar um assembly de nome forte](../../standard/assembly/reference-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="58997-115">For more information, see [How to: Reference a strong-named assembly](../../standard/assembly/reference-strong-named.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58997-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="58997-116">See also</span></span>

- [<span data-ttu-id="58997-117">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="58997-117">C# programming guide</span></span>](../../../api/index.md)
- [<span data-ttu-id="58997-118">Conceitos de programação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58997-118">Programming concepts (Visual Basic)</span></span>](../../../api/index.md)
- [<span data-ttu-id="58997-119">Programar com assemblies</span><span class="sxs-lookup"><span data-stu-id="58997-119">Program with assemblies</span></span>](../../standard/assembly/index.md)
