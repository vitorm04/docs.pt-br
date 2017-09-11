---
title: 'Como: compartilhar um Assembly com outros aplicativos (Visual Basic) | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ceebb3934c269284db18c9ca8e561417eaf5baa1
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a><span data-ttu-id="8d283-102">Como: compartilhar um Assembly com outros aplicativos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d283-102">How to: Share an Assembly with Other Applications (Visual Basic)</span></span>
<span data-ttu-id="8d283-103">Os assemblies podem ser particulares ou compartilhados: por padrão, a maioria dos programas simples consistem em um conjunto de módulos particular porque eles não se destina a ser usado por outros aplicativos.</span><span class="sxs-lookup"><span data-stu-id="8d283-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="8d283-104">Para compartilhar um assembly com outros aplicativos, ele deve ser colocado no [Global Assembly Cache](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) (GAC).</span><span class="sxs-lookup"><span data-stu-id="8d283-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="8d283-105">Compartilhamento de um assembly</span><span class="sxs-lookup"><span data-stu-id="8d283-105">Sharing an assembly</span></span>  
  
1.  <span data-ttu-id="8d283-106">Crie o assembly.</span><span class="sxs-lookup"><span data-stu-id="8d283-106">Create your assembly.</span></span> <span data-ttu-id="8d283-107">Para obter mais informações, consulte [Criando Assemblies](http://msdn.microsoft.com/library/54832ee9-dca8-4c8b-913c-c0b9d265e9a4).</span><span class="sxs-lookup"><span data-stu-id="8d283-107">For more information, see [Creating Assemblies](http://msdn.microsoft.com/library/54832ee9-dca8-4c8b-913c-c0b9d265e9a4).</span></span>  
  
2.  <span data-ttu-id="8d283-108">Atribua um nome forte ao assembly.</span><span class="sxs-lookup"><span data-stu-id="8d283-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="8d283-109">Para obter mais informações, consulte [como: assinar um Assembly com um nome forte](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67).</span><span class="sxs-lookup"><span data-stu-id="8d283-109">For more information, see [How to: Sign an Assembly with a Strong Name](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67).</span></span>  
  
3.  <span data-ttu-id="8d283-110">Atribua informações de versão para o assembly.</span><span class="sxs-lookup"><span data-stu-id="8d283-110">Assign version information to your assembly.</span></span> <span data-ttu-id="8d283-111">Para obter mais informações, consulte [controle de versão do Assembly](https://msdn.microsoft.com/library/51ket42z).</span><span class="sxs-lookup"><span data-stu-id="8d283-111">For more information, see [Assembly Versioning](https://msdn.microsoft.com/library/51ket42z).</span></span>  
  
4.  <span data-ttu-id="8d283-112">Adicione o assembly no cache de Assembly Global.</span><span class="sxs-lookup"><span data-stu-id="8d283-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="8d283-113">Para obter mais informações, consulte [como: instalar um Assembly no Cache de Assembly Global](http://msdn.microsoft.com/library/a7e6f091-d02c-49ba-b736-7295cb0eb743).</span><span class="sxs-lookup"><span data-stu-id="8d283-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](http://msdn.microsoft.com/library/a7e6f091-d02c-49ba-b736-7295cb0eb743).</span></span>  
  
5.  <span data-ttu-id="8d283-114">Acesse os tipos contidos no assembly de outros aplicativos.</span><span class="sxs-lookup"><span data-stu-id="8d283-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="8d283-115">Para obter mais informações, consulte [como: referenciar um Assembly de nome forte](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span><span class="sxs-lookup"><span data-stu-id="8d283-115">For more information, see [How to: Reference a Strong-Named Assembly](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d283-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d283-116">See Also</span></span>  
 <span data-ttu-id="8d283-117">[Conceitos de programação](../../../../visual-basic/programming-guide/concepts/index.md)
 [Assemblies e o Cache de Assembly Global (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="8d283-117">[Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md)
 [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="8d283-118"> [Programação com Assemblies](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6)</span><span class="sxs-lookup"><span data-stu-id="8d283-118"> [Programming with Assemblies](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6)</span></span>
