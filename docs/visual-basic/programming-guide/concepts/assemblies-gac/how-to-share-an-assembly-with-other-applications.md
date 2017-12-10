---
title: 'Como: compartilhar um Assembly com outros aplicativos (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0ad7a3f2ee82d0a582e755035448d565a9a8cb9d
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a><span data-ttu-id="4d85f-102">Como: compartilhar um Assembly com outros aplicativos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d85f-102">How to: Share an Assembly with Other Applications (Visual Basic)</span></span>
<span data-ttu-id="4d85f-103">Os assemblies podem ser particulares ou compartilhados: por padrão, a maioria dos programas simples consistem em um assembly particular porque eles não se destinam a serem usados por outros aplicativos.</span><span class="sxs-lookup"><span data-stu-id="4d85f-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="4d85f-104">Para compartilhar um assembly com outros aplicativos, ele deve ser colocado no [GAC](../../../../framework/app-domains/gac.md) (Cache de Assembly Global).</span><span class="sxs-lookup"><span data-stu-id="4d85f-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="4d85f-105">Compartilhando um assembly</span><span class="sxs-lookup"><span data-stu-id="4d85f-105">Sharing an assembly</span></span>  
  
1.  <span data-ttu-id="4d85f-106">Crie o assembly.</span><span class="sxs-lookup"><span data-stu-id="4d85f-106">Create your assembly.</span></span> <span data-ttu-id="4d85f-107">Para obter mais informações, consulte [Criando assemblies](../../../../framework/app-domains/create-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="4d85f-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2.  <span data-ttu-id="4d85f-108">Atribua um nome forte ao assembly.</span><span class="sxs-lookup"><span data-stu-id="4d85f-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="4d85f-109">Para obter mais informações, consulte [Como assinar um assembly com um nome forte](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="4d85f-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3.  <span data-ttu-id="4d85f-110">Atribua informações de versão ao assembly.</span><span class="sxs-lookup"><span data-stu-id="4d85f-110">Assign version information to your assembly.</span></span> <span data-ttu-id="4d85f-111">Para obter mais informações, consulte [Controle de versão do assembly](../../../../../docs/framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="4d85f-111">For more information, see [Assembly Versioning](../../../../../docs/framework/app-domains/assembly-versioning.md).</span></span>  
  
4.  <span data-ttu-id="4d85f-112">Adicione o assembly no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="4d85f-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="4d85f-113">Para obter mais informações, consulte [Como instalar um assembly no cache de assembly global](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="4d85f-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5.  <span data-ttu-id="4d85f-114">Acesse, de outros aplicativos, os tipos contidos no assembly.</span><span class="sxs-lookup"><span data-stu-id="4d85f-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="4d85f-115">Para obter mais informações, consulte [Como referenciar um assembly de nome forte](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span><span class="sxs-lookup"><span data-stu-id="4d85f-115">For more information, see [How to: Reference a Strong-Named Assembly](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d85f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d85f-116">See Also</span></span>  
 <span data-ttu-id="4d85f-117">[Conceitos de programação](../../../../visual-basic/programming-guide/concepts/index.md) [Assemblies e Cache de Assembly Global (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)</span><span class="sxs-lookup"><span data-stu-id="4d85f-117">[Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md) [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)</span></span>  
 [<span data-ttu-id="4d85f-118">Programação com assemblies</span><span class="sxs-lookup"><span data-stu-id="4d85f-118">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
