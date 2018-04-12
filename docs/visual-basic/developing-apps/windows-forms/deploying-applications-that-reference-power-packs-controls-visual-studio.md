---
title: Implantando aplicativos que referenciam controles de Power Packs (Visual Studio)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Power Packs, deploying
ms.assetid: f2230f53-a745-4731-89e6-033943faa209
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2a9562acf05cd27eed7bc1ad963845af9a7ca5f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="deploying-applications-that-reference-power-packs-controls-visual-studio"></a><span data-ttu-id="23df8-102">Implantando aplicativos que referenciam controles de Power Packs (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="23df8-102">Deploying applications that reference Power Packs controls (Visual Studio)</span></span>
<span data-ttu-id="23df8-103">Se você deseja implantar um aplicativo que faz referência os controles de Power Packs (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, ou <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), os controles devem ser instalados no computador de destino.</span><span class="sxs-lookup"><span data-stu-id="23df8-103">If you want to deploy an application that references the Power Packs controls (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, or <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), the controls must be installed on the destination computer.</span></span>  
  
## <a name="installing-the-power-packs-controls-as-a-prerequisite"></a><span data-ttu-id="23df8-104">Instalando os controles de Power Packs como um pré-requisito</span><span class="sxs-lookup"><span data-stu-id="23df8-104">Installing the Power Packs controls as a prerequisite</span></span>  
 <span data-ttu-id="23df8-105">Para implantar um aplicativo, você também deve implantar todos os componentes que são referenciados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="23df8-105">To successfully deploy an application, you must also deploy all components that are referenced by the application.</span></span> <span data-ttu-id="23df8-106">O processo de instalação de componentes de pré-requisito é conhecido como *inicializar*.</span><span class="sxs-lookup"><span data-stu-id="23df8-106">The process of installing prerequisite components is known as *bootstrapping*.</span></span>  
  
 <span data-ttu-id="23df8-107">Quando [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] está instalado no computador de desenvolvimento, um pacote de bootstrapper é adicionado de Power Packs o [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] directory bootstrapper.</span><span class="sxs-lookup"><span data-stu-id="23df8-107">When [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] is installed on your development computer, a Power Packs bootstrapper package is added to the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] bootstrapper directory.</span></span> <span data-ttu-id="23df8-108">Este pacote está disponível, em seguida, quando você seguir os procedimentos para adicionar pré-requisitos para o [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] ou implantação do Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="23df8-108">This package is then available when you follow the procedures for adding prerequisites for either [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] or Windows Installer deployment.</span></span>  
  
 <span data-ttu-id="23df8-109">Por padrão, inicializar componentes são implantados no mesmo local que o pacote de instalação.</span><span class="sxs-lookup"><span data-stu-id="23df8-109">By default, bootstrapped components are deployed from the same location as the installation package.</span></span> <span data-ttu-id="23df8-110">Como alternativa, você pode optar por implantar os componentes de um local de compartilhamento de arquivo ou URL da qual os usuários podem baixá-las conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="23df8-110">Alternatively, you can choose to deploy the components from a URL or file share location from which users can download them as necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23df8-111">Para instalar componentes inicializados, o usuário talvez precise de permissões de usuário administrativo ou semelhante no computador.</span><span class="sxs-lookup"><span data-stu-id="23df8-111">To install bootstrapped components, the user might need administrative or similar user permissions on the computer.</span></span> <span data-ttu-id="23df8-112">Para [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] aplicativos, isso significa que o usuário deverá ter permissões administrativas para instalar o aplicativo, independentemente do nível de segurança especificado pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="23df8-112">For [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] applications, this means that the user will need administrative permissions to install the application, regardless of the security level specified by the application.</span></span> <span data-ttu-id="23df8-113">Depois que o aplicativo é instalado, o usuário pode executar o aplicativo sem permissões administrativas.</span><span class="sxs-lookup"><span data-stu-id="23df8-113">After the application is installed, the user can run the application without administrative permissions.</span></span>  
  
 <span data-ttu-id="23df8-114">Durante a instalação, os usuários serão solicitados a instalar os controles de Power Packs se eles não estiverem presentes no computador de destino.</span><span class="sxs-lookup"><span data-stu-id="23df8-114">During installation, users will be prompted to install the Power Packs controls if they are not present on the destination computer.</span></span>  
  
 <span data-ttu-id="23df8-115">Como alternativa para inicializar, você pode implantar previamente os controles de Power Packs usando um sistema de distribuição eletrônica de software, como o Microsoft Systems Management Server.</span><span class="sxs-lookup"><span data-stu-id="23df8-115">As an alternative to bootstrapping, you can pre-deploy the Power Packs controls by using an electronic software distribution system such as Microsoft Systems Management Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23df8-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23df8-116">See also</span></span>  
 [<span data-ttu-id="23df8-117">Como instalar pré-requisitos com um aplicativo ClickOnce</span><span class="sxs-lookup"><span data-stu-id="23df8-117">How to: Install Prerequisites with a ClickOnce Application</span></span>](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [<span data-ttu-id="23df8-118">Controles de Power Packs do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="23df8-118">Visual Basic Power Packs Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)
