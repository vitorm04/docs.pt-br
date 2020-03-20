---
title: Autorizando o acesso às operações de serviço
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: c2ad6977674666ef65df1ea4cfe58cfd4bff8b69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183918"
---
# <a name="authorizing-access-to-service-operations"></a>Autorizando o acesso às operações de serviço
Esta amostra demonstra como usar o <xref:System.Security.Permissions.PrincipalPermissionAttribute> [ \<serviçoAutorização>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) para permitir o uso do atributo para autorizar o acesso às operações de serviço. Esta amostra é baseada na amostra [Getting Started.](../../../../docs/framework/wcf/samples/getting-started-sample.md) O serviço e o cliente são configurados usando o [ \<>wsHttpBinding ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). O `mode` atributo [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) da>de `Message` `clientCredentialType` segurança foi `Windows`definido e foi definido para . O <xref:System.Security.Permissions.PrincipalPermissionAttribute> é aplicado a cada método de serviço e usado para restringir o acesso a cada operação. O chamador deve ser um administrador do Windows para acessar cada operação.  
  
 Nesta amostra, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 O arquivo de configuração do serviço `principalPermissionMode` usa o [ \<serviçoAutorização>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) para definir o atributo:  
  
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
  
 A `principalPermissionMode` configuração do `UseWindowsGroups` <xref:System.Security.Permissions.PrincipalPermissionAttribute> "para" permite o uso de com base em nomes de grupos do Windows.  
  
 O <xref:System.Security.Permissions.PrincipalPermissionAttribute> é aplicado a cada operação para exigir que o chamador faça parte do grupo de administradores do Windows, conforme mostrado no código de amostra a seguir.  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente. O cliente se comunica com sucesso com cada operação se estiver executando uma conta que faz parte do grupo Administradores; caso contrário, o acesso é negado. Para experimentar a falha de autorização, execute o cliente em uma conta que não faz parte do grupo Administradores. Pressione ENTER na janela do console para desligar o cliente.  
  
 Um serviço pode ser notificado de falhas <xref:System.ServiceModel.Dispatcher.IErrorHandler>de autorização implementando um . Consulte [Estendendo o controle sobre o manuseio de erros e relatórios](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) para obter informações sobre a implementação `IErrorHandler`.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de computador único ou cruzado, siga as instruções em [Executar as amostras da Fundação](../../../../docs/framework/wcf/samples/running-the-samples.md)de Comunicação do Windows .  
