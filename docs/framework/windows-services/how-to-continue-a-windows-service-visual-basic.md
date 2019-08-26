---
title: 'Como: Continuar um serviço Windows (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- ServiceController.Continue
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: e5d13760-4c83-4b0d-abef-39852677cd7a
author: ghogen
ms.openlocfilehash: c9a783c0e7df39381ad1d9a8fedd7419605fd241
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935552"
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a><span data-ttu-id="dcc68-102">Como: Continuar um serviço Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dcc68-102">How to: Continue a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="dcc68-103">Este exemplo usa o componente <xref:System.ServiceProcess.ServiceController> para continuar o serviço de administração do IIS no computador local.</span><span class="sxs-lookup"><span data-stu-id="dcc68-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to continue the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dcc68-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dcc68-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 <span data-ttu-id="dcc68-105">Este exemplo de código também está disponível como um snippet de código do IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="dcc68-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="dcc68-106">No selecionador de snippet de código, ele está localizado em **Sistema Operacional Windows &gt; Serviços Windows**.</span><span class="sxs-lookup"><span data-stu-id="dcc68-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="dcc68-107">Para obter mais informações, consulte [Snippets de Código](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="dcc68-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dcc68-108">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="dcc68-108">Compiling the Code</span></span>  
 <span data-ttu-id="dcc68-109">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="dcc68-109">This example requires:</span></span>  
  
- <span data-ttu-id="dcc68-110">Uma referência do projeto para System.serviceprocess.dll.</span><span class="sxs-lookup"><span data-stu-id="dcc68-110">A project reference to System.serviceprocess.dll.</span></span>  
  
- <span data-ttu-id="dcc68-111">Acesso aos membros do namespace <xref:System.ServiceProcess>.</span><span class="sxs-lookup"><span data-stu-id="dcc68-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="dcc68-112">Adicione uma instrução `Imports` se você não está qualificando totalmente os nomes de membros em seu código.</span><span class="sxs-lookup"><span data-stu-id="dcc68-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="dcc68-113">Para obter mais informações, consulte [Instrução Imports (tipo e namespace .NET)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="dcc68-113">For more information, see [Imports Statement (.NET Namespace and Type)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="dcc68-114">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="dcc68-114">Robust Programming</span></span>  
 <span data-ttu-id="dcc68-115">A propriedade <xref:System.ServiceProcess.ServiceController.MachineName%2A> da classe <xref:System.ServiceProcess.ServiceController> é o computador local por padrão.</span><span class="sxs-lookup"><span data-stu-id="dcc68-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="dcc68-116">Para referenciar os Serviços Windows em outro computador, altere a propriedade <xref:System.ServiceProcess.ServiceController.MachineName%2A> para o nome desse computador.</span><span class="sxs-lookup"><span data-stu-id="dcc68-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="dcc68-117">Não é possível chamar o método <xref:System.ServiceProcess.ServiceController.Continue%2A> em um serviço até que o status do controlador de serviço seja <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span><span class="sxs-lookup"><span data-stu-id="dcc68-117">You cannot call the <xref:System.ServiceProcess.ServiceController.Continue%2A> method on a service until the service controller status is <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span></span>  
  
 <span data-ttu-id="dcc68-118">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="dcc68-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="dcc68-119">O serviço não pode ser retomado.</span><span class="sxs-lookup"><span data-stu-id="dcc68-119">The service cannot be resumed.</span></span> <span data-ttu-id="dcc68-120">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="dcc68-120">(<xref:System.InvalidOperationException>)</span></span>  
  
- <span data-ttu-id="dcc68-121">Ocorreu um erro ao acessar uma API do sistema.</span><span class="sxs-lookup"><span data-stu-id="dcc68-121">An error occurred when accessing a system API.</span></span> <span data-ttu-id="dcc68-122">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="dcc68-122">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="dcc68-123">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="dcc68-123">.NET Framework Security</span></span>  
 <span data-ttu-id="dcc68-124">O controle de serviços no computador pode ser restringido usando a enumeração <xref:System.ServiceProcess.ServiceControllerPermissionAccess> para definir permissões na classe <xref:System.ServiceProcess.ServiceControllerPermission>.</span><span class="sxs-lookup"><span data-stu-id="dcc68-124">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> enumeration to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission> class.</span></span>  
  
 <span data-ttu-id="dcc68-125">O acesso a informações de serviço pode ser restringido usando a enumeração <xref:System.Security.Permissions.PermissionState> para definir permissões na classe <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="dcc68-125">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> enumeration to set permissions in the <xref:System.Security.Permissions.SecurityPermission> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcc68-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dcc68-126">See also</span></span>

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- [<span data-ttu-id="dcc68-127">Como: Pausar um Serviço Windows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dcc68-127">How to: Pause a Windows Service (Visual Basic)</span></span>](../../../docs/framework/windows-services/how-to-pause-a-windows-service-visual-basic.md)
