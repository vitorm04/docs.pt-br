---
title: Como continuar um Serviço Windows (Visual Basic)
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
manager: douge
ms.openlocfilehash: 15ef15e0afe43d56db0972a686cd093e22c672dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a>Como continuar um Serviço Windows (Visual Basic)
Este exemplo usa o <xref:System.ServiceProcess.ServiceController> componente para continuar o serviço de administração do IIS no computador local.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 Este exemplo de código também está disponível como um trecho de código do IntelliSense. No selecionador de trecho de código, ele está localizado em **sistema operacional Windows > Windows Services**. Para obter mais informações, consulte [Trechos de Código](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Uma referência de projeto para System.serviceprocess.dll.  
  
-   Acesso aos membros do namespace <xref:System.ServiceProcess>. Adicione uma instrução `Imports` se você não está qualificando totalmente os nomes de membros em seu código. Para obter mais informações, consulte [Instrução Imports (tipo e namespace .NET)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Programação robusta  
 O <xref:System.ServiceProcess.ServiceController.MachineName%2A> propriedade o <xref:System.ServiceProcess.ServiceController> classe é o computador local por padrão. Para fazer referência a serviços do Windows em outro computador, altere o <xref:System.ServiceProcess.ServiceController.MachineName%2A> propriedade para o nome do computador.  
  
 Não é possível chamar o <xref:System.ServiceProcess.ServiceController.Continue%2A> método em um serviço até que o status do controlador de serviço é <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.  
  
 As seguintes condições podem causar uma exceção:  
  
-   O serviço não pode ser retomado. (<xref:System.InvalidOperationException>)  
  
-   Ocorreu um erro ao acessar uma API do sistema. (<xref:System.ComponentModel.Win32Exception>)  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Controle de serviços no computador pode ser restrito usando o <xref:System.ServiceProcess.ServiceControllerPermissionAccess> enumeração para definir permissões na <xref:System.ServiceProcess.ServiceControllerPermission> classe.  
  
 Acesso a informações de serviço pode ser restrita usando o <xref:System.Security.Permissions.PermissionState> enumeração para definir permissões na <xref:System.Security.Permissions.SecurityPermission> classe.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceProcess.ServiceController>  
 <xref:System.ServiceProcess.ServiceControllerStatus>  
 [Como Pausar um Serviço Windows (Visual Basic)](../../../docs/framework/windows-services/how-to-pause-a-windows-service-visual-basic.md)
