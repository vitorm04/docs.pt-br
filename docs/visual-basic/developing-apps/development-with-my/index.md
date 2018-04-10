---
title: Desenvolvimento com My (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.MyWpfExtension.Windows
helpviewer_keywords:
- My object
- My namespace
- My feature
- Visual Basic, programming in
ms.assetid: f1d04509-5e46-4551-9f9f-94334a121fca
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2cf51e1f6292a61c071fe6d92f5fcbce4be84ff4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="development-with-my-visual-basic"></a><span data-ttu-id="81276-102">Desenvolvimento com My (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81276-102">Development with My (Visual Basic)</span></span>
<span data-ttu-id="81276-103">O Visual Basic apresenta novos recursos para o método RAD que aumentam a produtividade, facilitam o uso e dão mais robustez.</span><span class="sxs-lookup"><span data-stu-id="81276-103">Visual Basic provides new features for rapid application development that improve productivity and ease of use while delivering power.</span></span> <span data-ttu-id="81276-104">Um desses recursos, chamado `My`, oferece acesso a informações e a instâncias de objeto padrão relacionadas ao aplicativo e ao seu ambiente de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="81276-104">One of these features, called `My`, provides access to information and default object instances that are related to the application and its run-time environment.</span></span> <span data-ttu-id="81276-105">Essas informações são organizadas em um formato que pode ser descoberto por meio do IntelliSense e que é logicamente delineado de acordo com o uso.</span><span class="sxs-lookup"><span data-stu-id="81276-105">This information is organized in a format that is discoverable through IntelliSense and logically delineated according to use.</span></span>  
  
 <span data-ttu-id="81276-106">Os membros de alto nível do `My` são expostos como objetos.</span><span class="sxs-lookup"><span data-stu-id="81276-106">Top-level members of `My` are exposed as objects.</span></span> <span data-ttu-id="81276-107">Cada objeto se comporta de forma semelhante a um namespace ou uma classe com membros `Shared` e um conjunto de membros relacionados são expostos.</span><span class="sxs-lookup"><span data-stu-id="81276-107">Each object behaves similarly to a namespace or a class with `Shared` members, and it exposes a set of related members.</span></span>  
  
 <span data-ttu-id="81276-108">Esta tabela mostra objetos `My` de nível superior e suas relações uns com os outros.</span><span class="sxs-lookup"><span data-stu-id="81276-108">This table shows the top-level `My` objects and their relationship to each other.</span></span>  
  
 <span data-ttu-id="81276-109">![Modelo d objeto para My](../../../visual-basic/developing-apps/development-with-my/media/myobjmodel.gif "MyObjModel")</span><span class="sxs-lookup"><span data-stu-id="81276-109">![Object Model for My](../../../visual-basic/developing-apps/development-with-my/media/myobjmodel.gif "MyObjModel")</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="81276-110">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="81276-110">In This Section</span></span>  
 [<span data-ttu-id="81276-111">Executando tarefas com My.Application, My.Computer e My.User</span><span class="sxs-lookup"><span data-stu-id="81276-111">Performing Tasks with My.Application, My.Computer, and My.User</span></span>](../../../visual-basic/developing-apps/development-with-my/performing-tasks-with-my-application-my-computer-and-my-user.md)  
 <span data-ttu-id="81276-112">Descreve os três objetos `My` centrais `My.Application`, `My.Computer` e `My.User`, que fornecem acesso a informações e funcionalidade</span><span class="sxs-lookup"><span data-stu-id="81276-112">Describes the three central `My` objects, `My.Application`, `My.Computer`, and `My.User`, which provide access to information and functionality</span></span>  
  
 [<span data-ttu-id="81276-113">Instâncias de objeto padrão fornecidas por My.Forms e My.WebServices</span><span class="sxs-lookup"><span data-stu-id="81276-113">Default Object Instances Provided by My.Forms and My.WebServices</span></span>](../../../visual-basic/developing-apps/development-with-my/default-object-instances-provided-by-my-forms-and-my-webservices.md)  
 <span data-ttu-id="81276-114">Descreve os objetos `My.Forms` e `My.WebServices`, que fornecem acesso a formulários, fontes de dados e serviços Web XML usados por seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="81276-114">Describes the `My.Forms` and `My.WebServices` objects, which provide access to forms, data sources, and XML Web services used by your application.</span></span>  
  
 [<span data-ttu-id="81276-115">Método RAD com My.Resources e My.Settings</span><span class="sxs-lookup"><span data-stu-id="81276-115">Rapid Application Development with My.Resources and My.Settings</span></span>](../../../visual-basic/developing-apps/development-with-my/rapid-application-development-with-my-resources-and-my-settings.md)  
 <span data-ttu-id="81276-116">Descreve os objetos `My.Resources` e `My.Settings`, que fornecem acesso a recursos e configurações de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="81276-116">Describes the `My.Resources` and `My.Settings` objects, which provide access to an application's resources and settings.</span></span>  
  
 [<span data-ttu-id="81276-117">Visão geral do modelo de aplicativo do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="81276-117">Overview of the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)  
 <span data-ttu-id="81276-118">Descreve o modelo [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] de inicialização/desligamento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="81276-118">Describes the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Application Startup/Shutdown model.</span></span>  
  
 [<span data-ttu-id="81276-119">Como My depende do tipo de projeto</span><span class="sxs-lookup"><span data-stu-id="81276-119">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)  
 <span data-ttu-id="81276-120">Fornece detalhes sobre quais os recursos `My` que estão disponíveis em diferentes tipos de projeto.</span><span class="sxs-lookup"><span data-stu-id="81276-120">Gives details on which `My` features are available in different project types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81276-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81276-121">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>  
 [<span data-ttu-id="81276-122">Objeto My.Forms</span><span class="sxs-lookup"><span data-stu-id="81276-122">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)  
 [<span data-ttu-id="81276-123">Objeto My.WebServices</span><span class="sxs-lookup"><span data-stu-id="81276-123">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)  
 [<span data-ttu-id="81276-124">Como My depende do tipo de projeto</span><span class="sxs-lookup"><span data-stu-id="81276-124">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
