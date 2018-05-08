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
manager: douge
ms.openlocfilehash: 43a852f1b618582c5aa65636e0a529434f8fd6a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a>Como pausar um Serviço Windows (Visual Basic)
Este exemplo usa o <xref:System.ServiceProcess.ServiceController> componente para pausar o serviço de administração do IIS no computador local.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 Este exemplo de código também está disponível como um trecho de código do IntelliSense. No selecionador de trecho de código, ele está localizado em **sistema operacional Windows > Windows Services**. Para obter mais informações, consulte [Trechos de Código](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Uma referência de projeto para System.serviceprocess.dll.  
  
-   Acesso aos membros do namespace <xref:System.ServiceProcess>. Adicione uma instrução `Imports` se você não está qualificando totalmente os nomes de membros em seu código. Para obter mais informações, consulte [Instrução Imports (tipo e namespace .NET)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Programação robusta  
 O <xref:System.ServiceProcess.ServiceController.MachineName%2A> propriedade o <xref:System.ServiceProcess.ServiceController> classe é o computador local por padrão. Para fazer referência a serviços do Windows em outro computador, altere o <xref:System.ServiceProcess.ServiceController.MachineName%2A> propriedade para o nome do computador.  
  
 As seguintes condições podem causar uma exceção:  
  
-   O serviço não pode ser pausado. (<xref:System.InvalidOperationException>)  
  
-   Ocorreu um erro ao acessar uma API do sistema. (<xref:System.ComponentModel.Win32Exception>)  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Controle de serviços no computador pode ser restrito usando o <xref:System.ServiceProcess.ServiceControllerPermissionAccess> para definir permissões no <xref:System.ServiceProcess.ServiceControllerPermission>.  
  
 Acesso a informações de serviço pode ser restrita usando o <xref:System.Security.Permissions.PermissionState> para definir permissões no <xref:System.Security.Permissions.SecurityPermission>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceProcess.ServiceController>  
 <xref:System.ServiceProcess.ServiceControllerStatus>  
 <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>  
 [Como Continuar um Serviço Windows (Visual Basic)](../../../docs/framework/windows-services/how-to-continue-a-windows-service-visual-basic.md)
