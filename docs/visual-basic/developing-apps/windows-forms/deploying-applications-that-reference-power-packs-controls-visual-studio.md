---
title: Implantando aplicativos que referenciam controles de Power Packs (Visual Studio) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Power Packs, deploying
ms.assetid: f2230f53-a745-4731-89e6-033943faa209
caps.latest.revision: 9
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
ms.openlocfilehash: ad1aba4f2e725abbe560f0c71fbb543e15741200
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="deploying-applications-that-reference-power-packs-controls-visual-studio"></a><span data-ttu-id="e3bc4-102">Implantando aplicativos que referenciam controles de Power Packs (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="e3bc4-102">Deploying applications that reference Power Packs controls (Visual Studio)</span></span>
<span data-ttu-id="e3bc4-103">Se você deseja implantar um aplicativo que faz referência aos controles de Power Packs (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, ou <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), os controles devem ser instalados no computador de destino.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> </xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> </xref:Microsoft.VisualBasic.PowerPacks.OvalShape> </xref:Microsoft.VisualBasic.PowerPacks.LineShape></span><span class="sxs-lookup"><span data-stu-id="e3bc4-103">If you want to deploy an application that references the Power Packs controls (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, or <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), the controls must be installed on the destination computer.</span></span>  
  
## <a name="installing-the-power-packs-controls-as-a-prerequisite"></a><span data-ttu-id="e3bc4-104">Instalação dos controles de Power Packs como um pré-requisito</span><span class="sxs-lookup"><span data-stu-id="e3bc4-104">Installing the Power Packs controls as a prerequisite</span></span>  
 <span data-ttu-id="e3bc4-105">Para implantar um aplicativo com êxito, você também deve implantar todos os componentes que são referenciados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e3bc4-105">To successfully deploy an application, you must also deploy all components that are referenced by the application.</span></span> <span data-ttu-id="e3bc4-106">O processo de instalação de componentes de pré-requisito é conhecido como *inicialização*.</span><span class="sxs-lookup"><span data-stu-id="e3bc4-106">The process of installing prerequisite components is known as *bootstrapping*.</span></span>  
  
 <span data-ttu-id="e3bc4-107">Quando [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] está instalado no computador de desenvolvimento, um pacote de bootstrapper é adicionado de Power Packs o [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] directory bootstrapper.</span><span class="sxs-lookup"><span data-stu-id="e3bc4-107">When [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] is installed on your development computer, a Power Packs bootstrapper package is added to the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] bootstrapper directory.</span></span> <span data-ttu-id="e3bc4-108">Este pacote estará disponível quando você seguir os procedimentos de adição de pré-requisitos para o [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] ou implantação do Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="e3bc4-108">This package is then available when you follow the procedures for adding prerequisites for either [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] or Windows Installer deployment.</span></span>  
  
 <span data-ttu-id="e3bc4-109">Por padrão, os componentes inicializados são implantados no mesmo local que o pacote de instalação.</span><span class="sxs-lookup"><span data-stu-id="e3bc4-109">By default, bootstrapped components are deployed from the same location as the installation package.</span></span> <span data-ttu-id="e3bc4-110">Como alternativa, você pode optar por implantar os componentes de um local de compartilhamento de arquivo ou URL da qual os usuários podem baixá-los conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="e3bc4-110">Alternatively, you can choose to deploy the components from a URL or file share location from which users can download them as necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3bc4-111">Para instalar componentes inicializados, o usuário talvez precise de permissões de usuário administrativo ou semelhante no computador.</span><span class="sxs-lookup"><span data-stu-id="e3bc4-111">To install bootstrapped components, the user might need administrative or similar user permissions on the computer.</span></span> <span data-ttu-id="e3bc4-112">Para [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] aplicativos, isso significa que o usuário deverá ter permissões administrativas para instalar o aplicativo, independentemente do nível de segurança especificado pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e3bc4-112">For [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] applications, this means that the user will need administrative permissions to install the application, regardless of the security level specified by the application.</span></span> <span data-ttu-id="e3bc4-113">Depois que o aplicativo é instalado, o usuário pode executar o aplicativo sem permissões administrativas.</span><span class="sxs-lookup"><span data-stu-id="e3bc4-113">After the application is installed, the user can run the application without administrative permissions.</span></span>  
  
 <span data-ttu-id="e3bc4-114">Durante a instalação, os usuários deverá instalar os controles de Power Packs se não estiverem presentes no computador de destino.</span><span class="sxs-lookup"><span data-stu-id="e3bc4-114">During installation, users will be prompted to install the Power Packs controls if they are not present on the destination computer.</span></span>  
  
 <span data-ttu-id="e3bc4-115">Como alternativa para a inicialização, você pode implantar previamente os controles de Power Packs usando um sistema de distribuição eletrônica de software, como o Microsoft Systems Management Server.</span><span class="sxs-lookup"><span data-stu-id="e3bc4-115">As an alternative to bootstrapping, you can pre-deploy the Power Packs controls by using an electronic software distribution system such as Microsoft Systems Management Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3bc4-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3bc4-116">See also</span></span>  
 <span data-ttu-id="e3bc4-117">[Como instalar pré-requisitos com um aplicativo ClickOnce](http://msdn.microsoft.com/library/e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5) </span><span class="sxs-lookup"><span data-stu-id="e3bc4-117">[How to: Install Prerequisites with a ClickOnce Application](http://msdn.microsoft.com/library/e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5) </span></span>  
<span data-ttu-id="e3bc4-118"> [Controles do Visual Basic Power Packs](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)</span><span class="sxs-lookup"><span data-stu-id="e3bc4-118"> [Visual Basic Power Packs Controls](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)</span></span>
