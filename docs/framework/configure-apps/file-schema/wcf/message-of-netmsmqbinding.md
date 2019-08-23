---
title: <message> de <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: b163dcb08e9656e3bde9c7fbb71fa1c92c9957ca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931512"
---
# <a name="message-of-netmsmqbinding"></a>\<> de mensagem \<de > de NetMsmqBinding

Define as configurações de segurança da mensagem SOAP `netMsmqBinding` nesta associação.

```xml
<system.ServiceModel>
  <bindings>
    <netMsmqBinding>
      <binding>
        <security>
          <message>
```

## <a name="syntax"></a>Sintaxe

```xml
<netMsmqBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
    </security>
  </binding>
</netMsmqBinding>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|algorithmSuite|Define a criptografia de mensagem e os algoritmos de encapsulamento de chaves que são usados para obter segurança baseada em mensagem para mensagens enviadas pelo transporte MSMQ.<br /><br /> O valor padrão é `Aes256`. Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.|
|clientCredentialType|Especifica o tipo de credencial a ser usado ao executar a autenticação de cliente para mensagens enviadas pelo transporte MSMQ. Os valores válidos incluem o seguinte:<br /><br /> None Isso permite que o serviço interaja com clientes anônimos. Nem o serviço nem o cliente exigem uma credencial.<br />Windows Isso permite que as trocas SOAP estejam sob o contexto autenticado de uma credencial do Windows. Isso sempre executa a autenticação baseada em Kerberos.<br />Usu Isso permite que o serviço exija que o cliente seja autenticado usando uma credencial de nome de usuário. A credencial, nesse caso, precisa ser especificada usando `clientCredentials` o comportamento **cuidado:**  O Windows Communication Foundation (WCF) não dá suporte ao envio de um resumo de senha ou à derivação de chaves usando a senha e o uso dessas chaves para segurança de mensagem. Portanto, o WCF impõe que a troca seja protegida ao usar credenciais de nome de usuário. Esse modo requer que o certificado de serviço seja especificado no lado do cliente `clientCredential` usando o `serviceCertificate`comportamento e. <br /><br /> Certificate Isso permite que o serviço exija que o cliente seja autenticado usando um certificado. Nesse caso, a credencial do cliente precisa ser especificada usando `clientCredentials` o comportamento. Nesse caso, a credencial de serviço precisa ser especificada usando `clientCredentials` o comportamento, especificando `serviceCertificate`o.<br />CardSpace Isso permite que o serviço exija que o cliente seja autenticado usando um CardSpace. O `serviceCertificate` deve ser provisionado `clientCredential` no comportamento.<br /><br /> O valor padrão é `Windows`. Esse atributo é do tipo <xref:System.ServiceModel.MessageCredentialType>.|

### <a name="child-elements"></a>Elementos filho

Nenhum

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[\<security>](security-of-netmsmqbinding.md)|Define as configurações de segurança para uma associação.|

## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [Filas no WCF](../../../wcf/feature-details/queues-in-wcf.md)
- [Protegendo serviços e clientes](../../../wcf/feature-details/securing-services-and-clients.md)
- [Associações](../../../wcf/bindings.md)
- [Configurando associações fornecidas pelo sistema](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Usando associações para configurar serviços e clientes](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../misc/binding.md)
