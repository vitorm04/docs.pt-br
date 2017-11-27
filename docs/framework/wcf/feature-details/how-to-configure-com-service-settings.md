---
title: "Como configurar configurações de serviço de COM+"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: COM+ [WCF], configuring service settings
ms.assetid: f42a55a8-3af8-4394-9fdd-bf12a93780eb
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7cbe038b55358ec8607d54b67861ef1743c2e301
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-configure-com-service-settings"></a>Como configurar configurações de serviço de COM+
Quando uma interface de aplicativo é adicionada ou removida usando a ferramenta de configuração do serviço COM+, a configuração do serviço Web é atualizada no arquivo de configuração do aplicativo. No modo de hospedados pelo COM+, o arquivo de config é colocado no diretório raiz do aplicativo (aplicativos de %PROGRAMFILES%\ComPlus\\{appid} é o padrão). Em ambos os modos hospedado na Web, o arquivo Web. config é colocado no diretório raiz virtual especificado.  
  
> [!NOTE]
>  Assinatura de mensagens deve ser usada para proteger contra falsificação de mensagens entre um cliente e um servidor. Além disso, a criptografia de camada de transporte ou a mensagem deve ser usada para proteger contra a divulgação de informações de mensagens entre um cliente e um servidor. Assim como acontece com [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services, você deve usar a limitação para limitar o número de chamadas simultâneas, conexões, instâncias e as operações pendentes. Isso ajuda a impedir o consumo excessivo de recursos. Comportamento de limitação é especificado por meio do arquivo de configuração do serviço.  
  
## <a name="example"></a>Exemplo  
 Considere a possibilidade de um componente que implementa a interface a seguir:  
  
```  
[Guid("C551FBA9-E3AA-4272-8C2A-84BD8D290AC7")]  
public interface IFinances  
{  
    string Debit(string accountNo, double amount);  
    string Credit(string accountNo, double amount);  
}  
```  
  
 Se o componente é exposto como um serviço Web, o contrato de serviço correspondente que é exposta, e que os clientes precisam estar em conformidade, é o seguinte:  
  
```  
[ServiceContract(Session = true,  
Namespace = "http://tempuri.org/C551FBA9-E3AA-4272-8C2A-84BD8D290AC7",  
Name = "IFinances")]  
public interface IFinancesContract : IDisposable  
{  
    [OperationContract]  
    string Debit(string accountNo, double amount);  
    [OperationContract]  
    string Credit(string accountNo, double amount);  
}  
```  
  
> [!NOTE]
>  IID faz parte do espaço para nome inicial para o contrato.  
  
 Aplicativos cliente que usam esse serviço precisa estar de acordo com este contrato, além de usar uma associação que é compatível com a especificada na configuração do aplicativo.  
  
 O exemplo de código a seguir mostra um arquivo de configuração padrão. Sendo um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço da Web, isso está em conformidade com o esquema de configuração de modelo de serviço padrão e pode ser editado da mesma maneira que outras [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] arquivos de configuração de serviços.  
  
 Modificações típicas inclui:  
  
-   Alterando o endereço de ponto de extremidade do formulário ComponentName/ApplicationName/InterfaceName padrão para um formato mais utilizável.  
  
-   Modificando o namespace do serviço do formulário "http://tempuri.org/InterfaceID" padrão a um formulário mais relevante.  
  
-   Alterar o ponto de extremidade para usar uma associação de transporte diferentes.  
  
     No COM+-caso hospedado, o transporte de pipes nomeados é usado por padrão, mas um transporte-machine como TCP pode ser usado em vez disso.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <netNamedPipeBinding>  
                <binding name="comNonTransactionalBinding" />  
                <binding name="comTransactionalBinding" transactionFlow="true" />  
            </netNamedPipeBinding>  
        </bindings>  
        <comContracts>  
            <comContract contract="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"  
                name="IFinances" namespace="http://tempuri.org/C551FBA9-E3AA-4272-8C2A-84BD8D290AC7"  
                requiresSession="true">  
                <exposedMethods>  
                    <add exposedMethod="Debit" />  
                    <add exposedMethod="Credit" />  
                </exposedMethods>  
            </comContract>  
        </comContracts>  
        <services>  
            <service name="{DCDB24CC-0B19-4534-95CD-FBBFF4D67DD9},{C942B840-AD54-4A44-B5F7-928130980AB9}">  
                <endpoint address="IFinances" binding="netNamedPipeBinding" bindingConfiguration="comNonTransactionalBinding"  
                    contract="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}" />  
                <host>  
                    <baseAddresses>  
                        <add baseAddress="net.pipe://localhost/ServiceModelDocSampleApp/ServiceModelDocSample.esFinance" />  
                    </baseAddresses>  
                </host>  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Integrando aplicativos COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
