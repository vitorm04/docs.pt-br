---
title: 'Como: compartilhar um Assembly com outros aplicativos (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
ms.openlocfilehash: a7f6b49e8389108528c44d7464a2e68149dfa940
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44062891"
---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a><span data-ttu-id="dfcc2-102">Como: compartilhar um Assembly com outros aplicativos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dfcc2-102">How to: Share an Assembly with Other Applications (Visual Basic)</span></span>
<span data-ttu-id="dfcc2-103">Os assemblies podem ser particulares ou compartilhados: por padrão, a maioria dos programas simples consistem em um assembly particular porque eles não se destinam a serem usados por outros aplicativos.</span><span class="sxs-lookup"><span data-stu-id="dfcc2-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="dfcc2-104">Para compartilhar um assembly com outros aplicativos, ele deve ser colocado no [GAC](../../../../framework/app-domains/gac.md) (Cache de Assembly Global).</span><span class="sxs-lookup"><span data-stu-id="dfcc2-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="dfcc2-105">Compartilhando um assembly</span><span class="sxs-lookup"><span data-stu-id="dfcc2-105">Sharing an assembly</span></span>  
  
1.  <span data-ttu-id="dfcc2-106">Crie o assembly.</span><span class="sxs-lookup"><span data-stu-id="dfcc2-106">Create your assembly.</span></span> <span data-ttu-id="dfcc2-107">Para obter mais informações, consulte [Criando assemblies](../../../../framework/app-domains/create-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="dfcc2-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2.  <span data-ttu-id="dfcc2-108">Atribua um nome forte ao assembly.</span><span class="sxs-lookup"><span data-stu-id="dfcc2-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="dfcc2-109">Para obter mais informações, consulte [Como assinar um assembly com um nome forte](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="dfcc2-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3.  <span data-ttu-id="dfcc2-110">Atribua informações de versão ao assembly.</span><span class="sxs-lookup"><span data-stu-id="dfcc2-110">Assign version information to your assembly.</span></span> <span data-ttu-id="dfcc2-111">Para obter mais informações, consulte [Controle de versão do assembly](../../../../framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="dfcc2-111">For more information, see [Assembly Versioning](../../../../framework/app-domains/assembly-versioning.md).</span></span>  
  
4.  <span data-ttu-id="dfcc2-112">Adicione o assembly no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="dfcc2-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="dfcc2-113">Para obter mais informações, consulte [Como instalar um assembly no cache de assembly global](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="dfcc2-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5.  <span data-ttu-id="dfcc2-114">Acesse, de outros aplicativos, os tipos contidos no assembly.</span><span class="sxs-lookup"><span data-stu-id="dfcc2-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="dfcc2-115">Para obter mais informações, consulte [Como referenciar um assembly de nome forte](https://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span><span class="sxs-lookup"><span data-stu-id="dfcc2-115">For more information, see [How to: Reference a Strong-Named Assembly](https://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfcc2-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dfcc2-116">See Also</span></span>  
 <span data-ttu-id="dfcc2-117">[Conceitos de programação](../../../../visual-basic/programming-guide/concepts/index.md) [Assemblies e Cache de Assembly Global (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)</span><span class="sxs-lookup"><span data-stu-id="dfcc2-117">[Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md) [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)</span></span>  
 [<span data-ttu-id="dfcc2-118">Programação com assemblies</span><span class="sxs-lookup"><span data-stu-id="dfcc2-118">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
