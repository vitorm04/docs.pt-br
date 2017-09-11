---
title: Implantando aplicativos que referenciam o componente PrintForm (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- PrintForm component [Visual Basic], deploying
ms.assetid: b595ea44-a712-4625-a761-190c64f59bbe
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 7b625e0c58653f1ee9a2d263d7d2d29ad3b2e3c1
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="deploying-applications-that-reference-the-printform-component-visual-basic"></a><span data-ttu-id="6692c-102">Implantando aplicativos que referenciam o componente PrintForm (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6692c-102">Deploying applications that reference the PrintForm component (Visual Basic)</span></span>
<span data-ttu-id="6692c-103">Se desejar implantar um aplicativo que faz referência a <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>componente, o componente deve ser instalado no computador de destino.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="6692c-103">If you want to deploy an application that references the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component, the component must be installed on the destination computer.</span></span>  
  
 <span data-ttu-id="6692c-104">Os controles PowerPack não estão mais incluídos no Visual Studio, mas você pode baixá-los no [Centro de Download](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="6692c-104">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
## <a name="installing-the-printform-as-a-prerequisite"></a><span data-ttu-id="6692c-105">Instalando o PrintForm como um pré-requisito</span><span class="sxs-lookup"><span data-stu-id="6692c-105">Installing the PrintForm as a prerequisite</span></span>  
 <span data-ttu-id="6692c-106">Para implantar um aplicativo com êxito, você também deve implantar todos os componentes que são referenciados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6692c-106">To successfully deploy an application, you must also deploy all components that are referenced by the application.</span></span> <span data-ttu-id="6692c-107">O processo de instalação de componentes de pré-requisito é conhecido como *inicialização*.</span><span class="sxs-lookup"><span data-stu-id="6692c-107">The process of installing prerequisite components is known as *bootstrapping*.</span></span>  
  
 <span data-ttu-id="6692c-108">Quando o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>componente é instalado em seu computador de desenvolvimento, um pacote de bootstrapper do Microsoft Visual Basic Power Packs é adicionado para o [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] directory bootstrapper.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="6692c-108">When the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is installed on your development computer, a Microsoft Visual Basic Power Packs bootstrapper package is added to the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] bootstrapper directory.</span></span> <span data-ttu-id="6692c-109">Este pacote estará disponível quando você seguir os procedimentos de adição de pré-requisitos para o [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] ou implantação do Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="6692c-109">This package is then available when you follow the procedures for adding prerequisites for either [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] or Windows Installer deployment.</span></span>  
  
 <span data-ttu-id="6692c-110">Por padrão, os componentes inicializados são implantados no mesmo local que o pacote de instalação.</span><span class="sxs-lookup"><span data-stu-id="6692c-110">By default, bootstrapped components are deployed from the same location as the installation package.</span></span> <span data-ttu-id="6692c-111">Como alternativa, você pode optar por implantar os componentes de um local de compartilhamento de arquivo ou URL da qual os usuários podem baixá-los conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="6692c-111">Alternatively, you can choose to deploy the components from a URL or file share location from which users can download them as necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6692c-112">Para instalar componentes inicializados, o usuário talvez precise de permissões de usuário administrativo ou semelhante no computador.</span><span class="sxs-lookup"><span data-stu-id="6692c-112">To install bootstrapped components, the user might need administrative or similar user permissions on the computer.</span></span> <span data-ttu-id="6692c-113">Para [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] aplicativos, isso significa que o usuário deverá ter permissões administrativas para instalar o aplicativo, independentemente do nível de segurança especificado pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6692c-113">For [!INCLUDE[ndptecclick](../../../visual-basic/developing-apps/printing/includes/ndptecclick_md.md)] applications, this means that the user will need administrative permissions to install the application, regardless of the security level specified by the application.</span></span> <span data-ttu-id="6692c-114">Depois que o aplicativo é instalado, o usuário pode executar o aplicativo sem permissões administrativas.</span><span class="sxs-lookup"><span data-stu-id="6692c-114">After the application is installed, the user can run the application without administrative permissions.</span></span>  
  
 <span data-ttu-id="6692c-115">Durante a instalação, os usuários serão solicitados a instalar o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>componente se ele não está presente no computador de destino.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="6692c-115">During installation, users will be prompted to install the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component if it is not present on the destination computer.</span></span>  
  
 <span data-ttu-id="6692c-116">Como alternativa para a inicialização, você pode implantar previamente o <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>componente usando um sistema de distribuição eletrônica de software como o Microsoft Systems Management Server.</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></span><span class="sxs-lookup"><span data-stu-id="6692c-116">As an alternative to bootstrapping, you can pre-deploy the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component by using an electronic software distribution system like Microsoft Systems Management Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6692c-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6692c-117">See also</span></span>  
 <span data-ttu-id="6692c-118">[Como instalar pré-requisitos com um aplicativo ClickOnce](http://msdn.microsoft.com/library/e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5) </span><span class="sxs-lookup"><span data-stu-id="6692c-118">[How to: Install Prerequisites with a ClickOnce Application](http://msdn.microsoft.com/library/e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5) </span></span>  
<span data-ttu-id="6692c-119"> [Componente PrintForm](../../../visual-basic/developing-apps/printing/printform-component.md)</span><span class="sxs-lookup"><span data-stu-id="6692c-119"> [PrintForm Component](../../../visual-basic/developing-apps/printing/printform-component.md)</span></span>
