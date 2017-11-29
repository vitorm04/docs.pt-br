---
title: "Considerações sobre quando hospedar um controle ActiveX em um Windows Form"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- ActiveX controls [Windows Forms], hosting
- Windows Forms, ActiveX controls
- Windows Forms, hosting ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 2509302d-a74e-484f-9890-2acdbfa67a68
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3ec828ca0b2bd8231d0baca72bf97bef566f2651
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="considerations-when-hosting-an-activex-control-on-a-windows-form"></a><span data-ttu-id="f575a-102">Considerações sobre quando hospedar um controle ActiveX em um Windows Form</span><span class="sxs-lookup"><span data-stu-id="f575a-102">Considerations When Hosting an ActiveX Control on a Windows Form</span></span>
<span data-ttu-id="f575a-103">Embora o Windows Forms tenha sido otimizada para hospedar controles dos Windows Forms, você ainda poderá usar controles ActiveX.</span><span class="sxs-lookup"><span data-stu-id="f575a-103">Although Windows Forms have been optimized to host Windows Forms controls, you can still use ActiveX controls.</span></span> <span data-ttu-id="f575a-104">Lembre-se das seguintes considerações ao planejar um aplicativo que usa os controles ActiveX:</span><span class="sxs-lookup"><span data-stu-id="f575a-104">Keep the following considerations in mind when planning an application that uses ActiveX controls:</span></span>  
  
-   <span data-ttu-id="f575a-105">**Segurança** O Common Language Runtime foi aprimorado em relação à segurança de acesso do código.</span><span class="sxs-lookup"><span data-stu-id="f575a-105">**Security** The common language runtime has been enhanced with regard to code access security.</span></span> <span data-ttu-id="f575a-106">Aplicativos que contém formulários dos Windows Forms podem ser executados em um ambiente totalmente confiável sem problemas e em um ambiente de confiança parcial com a maioria das funcionalidades acessíveis.</span><span class="sxs-lookup"><span data-stu-id="f575a-106">Applications featuring Windows Forms can run in a fully trusted environment without issue and in a semi-trusted environment with most of the functionality accessible.</span></span> <span data-ttu-id="f575a-107">Controles dos Windows Forms podem ser hospedados em um navegador sem complicações.</span><span class="sxs-lookup"><span data-stu-id="f575a-107">Windows Forms controls can be hosted in a browser with no complications.</span></span> <span data-ttu-id="f575a-108">No entanto, controles ActiveX nos Windows Forms não podem aproveitar essas melhorias de segurança.</span><span class="sxs-lookup"><span data-stu-id="f575a-108">However, ActiveX controls on Windows Forms cannot take advantage of these security enhancements.</span></span> <span data-ttu-id="f575a-109">A execução de um controle ActiveX requer permissão de código não gerenciado, que é definida com o <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="f575a-109">Running an ActiveX control requires unmanaged code permission, which is set with the <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="f575a-110">Para obter mais informações sobre segurança e a permissão de código não gerenciado, consulte <xref:System.Security.Permissions.SecurityPermissionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f575a-110">For more information about security and unmanaged code permission, see <xref:System.Security.Permissions.SecurityPermissionAttribute>.</span></span>  
  
-   <span data-ttu-id="f575a-111">**Custo total de propriedade** Controles ActiveX adicionados a um Windows Form são implantados com esse Windows Form integralmente, o que pode aumentar significativamente o tamanho do arquivo criado.</span><span class="sxs-lookup"><span data-stu-id="f575a-111">**Total Cost of Ownership** ActiveX controls added to a Windows Form are deployed with that Windows Form in their entirety, which can add significantly to the size of the file(s) created.</span></span> <span data-ttu-id="f575a-112">Além disso, usar controles ActiveX nos Windows Forms requer a gravação no Registro.</span><span class="sxs-lookup"><span data-stu-id="f575a-112">Additionally, using ActiveX controls on Windows Forms requires writing to the registry.</span></span> <span data-ttu-id="f575a-113">Isso é mais invasivo no computador do usuário que os controles dos Windows Forms, que não exigem isso.</span><span class="sxs-lookup"><span data-stu-id="f575a-113">This is more invasive to a user's computer than Windows Forms controls, which do not require this.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f575a-114">Trabalhar com um controle ActiveX requer o uso de um wrapper de interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="f575a-114">Working with an ActiveX control requires the use of a COM interop wrapper.</span></span> <span data-ttu-id="f575a-115">Para obter mais informações, consulte [Interoperabilidade COM em Visual Basic e Visual C#](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="f575a-115">For more information, see [COM Interoperability in Visual Basic and Visual C#](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f575a-116">Se o nome de um membro do controle ActiveX corresponde a um nome definido no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], em seguida, o importador de controle ActiveX será prefixar o nome do membro com **Ctl** quando ele cria o <xref:System.Windows.Forms.AxHost> classe derivada.</span><span class="sxs-lookup"><span data-stu-id="f575a-116">If the name of a member of the ActiveX control matches a name defined in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], then the ActiveX Control Importer will prefix the member name with **Ctl** when it creates the <xref:System.Windows.Forms.AxHost> derived class.</span></span> <span data-ttu-id="f575a-117">Por exemplo, se o controle ActiveX tiver um membro chamado **Layout**, ele será renomeado para **CtlLayout** na classe derivada de AxHost, pois o evento **Layout** é definido dentro do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f575a-117">For example, if your ActiveX control has a member named **Layout**, it is renamed **CtlLayout** in the AxHost-derived class because the **Layout** event is defined within the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f575a-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f575a-118">See Also</span></span>  
 [<span data-ttu-id="f575a-119">Como adicionar controles do ActiveX ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f575a-119">How to: Add ActiveX Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)  
 [<span data-ttu-id="f575a-120">Segurança de acesso do código</span><span class="sxs-lookup"><span data-stu-id="f575a-120">Code Access Security</span></span>](../../../../docs/framework/misc/code-access-security.md)  
 [<span data-ttu-id="f575a-121">Controles e objetos programáveis comparados em diversas linguagens e bibliotecas</span><span class="sxs-lookup"><span data-stu-id="f575a-121">Controls and Programmable Objects Compared in Various Languages and Libraries</span></span>](http://msdn.microsoft.com/en-us/021f2a1b-8247-4348-a5ad-e1d9ab23004b)  
 [<span data-ttu-id="f575a-122">Colocando controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f575a-122">Putting Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)  
 [<span data-ttu-id="f575a-123">Controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f575a-123">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)
