---
title: "Como continuar um Serviço Windows (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
f1_keywords: ServiceController.Continue
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: e5d13760-4c83-4b0d-abef-39852677cd7a
caps.latest.revision: "16"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: 28dbbf2376416a340ad7853c026b2f763f695dcb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a><span data-ttu-id="e5f70-102">Como continuar um Serviço Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5f70-102">How to: Continue a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="e5f70-103">Este exemplo usa o <xref:System.ServiceProcess.ServiceController> componente para continuar o serviço de administração do IIS no computador local.</span><span class="sxs-lookup"><span data-stu-id="e5f70-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to continue the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5f70-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e5f70-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 <span data-ttu-id="e5f70-105">Este exemplo de código também está disponível como um trecho de código do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="e5f70-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="e5f70-106">No selecionador de trecho de código, ele está localizado em **sistema operacional Windows > Windows Services**.</span><span class="sxs-lookup"><span data-stu-id="e5f70-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="e5f70-107">Para obter mais informações, consulte [Trechos de Código](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="e5f70-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e5f70-108">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="e5f70-108">Compiling the Code</span></span>  
 <span data-ttu-id="e5f70-109">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="e5f70-109">This example requires:</span></span>  
  
-   <span data-ttu-id="e5f70-110">Uma referência de projeto para System.serviceprocess.dll.</span><span class="sxs-lookup"><span data-stu-id="e5f70-110">A project reference to System.serviceprocess.dll.</span></span>  
  
-   <span data-ttu-id="e5f70-111">Acesso aos membros do namespace <xref:System.ServiceProcess>.</span><span class="sxs-lookup"><span data-stu-id="e5f70-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="e5f70-112">Adicione uma instrução `Imports` se você não está qualificando totalmente os nomes de membros em seu código.</span><span class="sxs-lookup"><span data-stu-id="e5f70-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="e5f70-113">Para obter mais informações, consulte [Instrução Imports (tipo e namespace .NET)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="e5f70-113">For more information, see [Imports Statement (.NET Namespace and Type)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e5f70-114">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="e5f70-114">Robust Programming</span></span>  
 <span data-ttu-id="e5f70-115">O <xref:System.ServiceProcess.ServiceController.MachineName%2A> propriedade o <xref:System.ServiceProcess.ServiceController> classe é o computador local por padrão.</span><span class="sxs-lookup"><span data-stu-id="e5f70-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="e5f70-116">Para fazer referência a serviços do Windows em outro computador, altere o <xref:System.ServiceProcess.ServiceController.MachineName%2A> propriedade para o nome do computador.</span><span class="sxs-lookup"><span data-stu-id="e5f70-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="e5f70-117">Não é possível chamar o <xref:System.ServiceProcess.ServiceController.Continue%2A> método em um serviço até que o status do controlador de serviço é <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span><span class="sxs-lookup"><span data-stu-id="e5f70-117">You cannot call the <xref:System.ServiceProcess.ServiceController.Continue%2A> method on a service until the service controller status is <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span></span>  
  
 <span data-ttu-id="e5f70-118">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="e5f70-118">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="e5f70-119">O serviço não pode ser retomado.</span><span class="sxs-lookup"><span data-stu-id="e5f70-119">The service cannot be resumed.</span></span> <span data-ttu-id="e5f70-120">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="e5f70-120">(<xref:System.InvalidOperationException>)</span></span>  
  
-   <span data-ttu-id="e5f70-121">Ocorreu um erro ao acessar uma API do sistema.</span><span class="sxs-lookup"><span data-stu-id="e5f70-121">An error occurred when accessing a system API.</span></span> <span data-ttu-id="e5f70-122">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="e5f70-122">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="e5f70-123">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e5f70-123">.NET Framework Security</span></span>  
 <span data-ttu-id="e5f70-124">Controle de serviços no computador pode ser restrito usando o <xref:System.ServiceProcess.ServiceControllerPermissionAccess> enumeração para definir permissões na <xref:System.ServiceProcess.ServiceControllerPermission> classe.</span><span class="sxs-lookup"><span data-stu-id="e5f70-124">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> enumeration to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission> class.</span></span>  
  
 <span data-ttu-id="e5f70-125">Acesso a informações de serviço pode ser restrita usando o <xref:System.Security.Permissions.PermissionState> enumeração para definir permissões na <xref:System.Security.Permissions.SecurityPermission> classe.</span><span class="sxs-lookup"><span data-stu-id="e5f70-125">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> enumeration to set permissions in the <xref:System.Security.Permissions.SecurityPermission> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5f70-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5f70-126">See Also</span></span>  
 <xref:System.ServiceProcess.ServiceController>  
 <xref:System.ServiceProcess.ServiceControllerStatus>  
 [<span data-ttu-id="e5f70-127">Como: pausar um serviço do Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5f70-127">How to: Pause a Windows Service (Visual Basic)</span></span>](../../../docs/framework/windows-services/how-to-pause-a-windows-service-visual-basic.md)
