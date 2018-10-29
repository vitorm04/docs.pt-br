---
title: Como pausar um Serviço Windows (Visual Basic)
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- ServiceController.Pause
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: eddb9409-942b-46b6-a2ce-fbd4c65f2790
author: ghogen
ms.openlocfilehash: c62de97439ecf90ebfcc14d9fea4c5ab52f6ef73
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48035117"
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a><span data-ttu-id="dbda2-102">Como pausar um Serviço Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dbda2-102">How to: Pause a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="dbda2-103">Este exemplo usa o componente <xref:System.ServiceProcess.ServiceController> para pausar o serviço de administração do IIS no computador local.</span><span class="sxs-lookup"><span data-stu-id="dbda2-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to pause the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbda2-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dbda2-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 <span data-ttu-id="dbda2-105">Este exemplo de código também está disponível como um snippet de código do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="dbda2-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="dbda2-106">No selecionador de snippet de código, ele está localizado em **Sistema Operacional Windows &gt; Serviços Windows**.</span><span class="sxs-lookup"><span data-stu-id="dbda2-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="dbda2-107">Para obter mais informações, consulte [Snippets de Código](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="dbda2-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dbda2-108">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="dbda2-108">Compiling the Code</span></span>  
 <span data-ttu-id="dbda2-109">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="dbda2-109">This example requires:</span></span>  
  
-   <span data-ttu-id="dbda2-110">Uma referência do projeto para System.serviceprocess.dll.</span><span class="sxs-lookup"><span data-stu-id="dbda2-110">A project reference to System.serviceprocess.dll.</span></span>  
  
-   <span data-ttu-id="dbda2-111">Acesso aos membros do namespace <xref:System.ServiceProcess>.</span><span class="sxs-lookup"><span data-stu-id="dbda2-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="dbda2-112">Adicione uma instrução `Imports` se você não está qualificando totalmente os nomes de membros em seu código.</span><span class="sxs-lookup"><span data-stu-id="dbda2-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="dbda2-113">Para obter mais informações, consulte [Instrução Imports (tipo e namespace .NET)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="dbda2-113">For more information, see [Imports Statement (.NET Namespace and Type)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="dbda2-114">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="dbda2-114">Robust Programming</span></span>  
 <span data-ttu-id="dbda2-115">A propriedade <xref:System.ServiceProcess.ServiceController.MachineName%2A> da classe <xref:System.ServiceProcess.ServiceController> é o computador local por padrão.</span><span class="sxs-lookup"><span data-stu-id="dbda2-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="dbda2-116">Para referenciar os Serviços Windows em outro computador, altere a propriedade <xref:System.ServiceProcess.ServiceController.MachineName%2A> para o nome desse computador.</span><span class="sxs-lookup"><span data-stu-id="dbda2-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="dbda2-117">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="dbda2-117">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="dbda2-118">O serviço não pode ser colocado em pausa.</span><span class="sxs-lookup"><span data-stu-id="dbda2-118">The service cannot be paused.</span></span> <span data-ttu-id="dbda2-119">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="dbda2-119">(<xref:System.InvalidOperationException>)</span></span>  
  
-   <span data-ttu-id="dbda2-120">Ocorreu um erro ao acessar uma API do sistema.</span><span class="sxs-lookup"><span data-stu-id="dbda2-120">An error occurred when accessing a system API.</span></span> <span data-ttu-id="dbda2-121">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="dbda2-121">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="dbda2-122">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="dbda2-122">.NET Framework Security</span></span>  
 <span data-ttu-id="dbda2-123">O controle de serviços no computador pode ser restringido usando o <xref:System.ServiceProcess.ServiceControllerPermissionAccess> para definir permissões no <xref:System.ServiceProcess.ServiceControllerPermission>.</span><span class="sxs-lookup"><span data-stu-id="dbda2-123">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission>.</span></span>  
  
 <span data-ttu-id="dbda2-124">O acesso a informações de serviço pode ser restringido usando o <xref:System.Security.Permissions.PermissionState> para definir permissões em <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="dbda2-124">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> to set permissions in the <xref:System.Security.Permissions.SecurityPermission>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbda2-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dbda2-125">See Also</span></span>  
 <xref:System.ServiceProcess.ServiceController>  
 <xref:System.ServiceProcess.ServiceControllerStatus>  
 <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>  
 [<span data-ttu-id="dbda2-126">Como Continuar um Serviço Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dbda2-126">How to: Continue a Windows Service (Visual Basic)</span></span>](../../../docs/framework/windows-services/how-to-continue-a-windows-service-visual-basic.md)
