---
title: Autorizando o acesso às operações de serviço
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: b7f8b9b5fc4e6524da49b4d3f23de90a123e92e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="authorizing-access-to-service-operations"></a>Autorizando o acesso às operações de serviço
Este exemplo demonstra como usar o [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) para habilitar o uso do <xref:System.Security.Permissions.PrincipalPermissionAttribute> atributo para autorizar o acesso a operações de serviço. Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) exemplo. O serviço e o cliente são configurados usando o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). O `mode` atributo do [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) foi definida como `Message` e `clientCredentialType` foi definida como `Windows`. O <xref:System.Security.Permissions.PrincipalPermissionAttribute> é aplicado a cada método de serviço e usado para restringir o acesso a cada operação. O chamador deve ser um administrador do Windows para acessar cada operação.  
  
 Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço é hospedado por serviços de informações da Internet (IIS).  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O arquivo de configuração de serviço usa o [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) para definir o `principalPermissionMode` atributo:  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior>   
      <!-- The serviceAuthorization behavior sets the  
           principalPermissionMode to UseWindowsGroups.  
           This puts a WindowsPrincipal on the current thread when a   
           service is invoked. -->  
      <serviceAuthorization principalPermissionMode="UseWindowsGroups" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Definindo o `principalPermissionMode` para `UseWindowsGroups` permite o uso de <xref:System.Security.Permissions.PrincipalPermissionAttribute> com base em nomes de grupo do Windows.  
  
 O <xref:System.Security.Permissions.PrincipalPermissionAttribute> é aplicado a cada operação para exigir que o chamador fazer parte do grupo de administradores do Windows, conforme mostrado no código de exemplo a seguir.  
  
```  
[PrincipalPermission(SecurityAction.Demand,   
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente. O cliente com êxito se comunica com cada operação se ele estiver em execução em uma conta que faça parte do grupo Administradores; Caso contrário, o acesso foi negado. Para fazer experiências com falha de autorização, execute o cliente em uma conta que não faz parte do grupo Administradores. Pressione ENTER na janela do console para desligar o cliente.  
  
 Um serviço pode ser notificado das falhas de autorização ao implementar um <xref:System.ServiceModel.Dispatcher.IErrorHandler>. Consulte [estendendo controle sobre tratamento de erros e emissão de relatórios](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) para obter informações sobre como implementar `IErrorHandler`.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Consulte também
