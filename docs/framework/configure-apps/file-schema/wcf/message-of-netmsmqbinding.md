---
title: <message> De <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: c623b7daf1e91c9c1800b9653525cd51b1087506
ms.sourcegitcommit: 5c2176883dc3107445702724a7caa7ac2f6cb0d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2019
ms.locfileid: "58890560"
---
# <a name="message-of-netmsmqbinding"></a>\<message> of \<netMsmqBinding>

Define as configurações de segurança de mensagem SOAP sobre isso `netMsmqBinding` associação.

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
|algorithmSuite|Define a mensagem de algoritmos de criptografia e encapsulamento de chave que são usados para fins de segurança baseada em mensagens para mensagens enviadas pelo transporte MSMQ.<br /><br /> O valor padrão é `Aes256`. Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.|
|clientCredentialType|Especifica o tipo de credencial a ser usada ao executar a autenticação de cliente para mensagens enviadas por meio do transporte MSMQ. Os valores válidos incluem o seguinte:<br /><br /> -None: Isso permite que o serviço interaja com clientes anônimos. Nem o serviço nem o cliente requer uma credencial.<br />-   Windows: Isso permite que as trocas SOAP estar sob o contexto autenticado de uma credencial do Windows. Isso sempre executa a autenticação Kerberos.<br />-Nome de usuário: Isso permite que o serviço exigir que o cliente seja autenticado usando uma credencial de nome de usuário. A credencial nesse caso, deve ser especificado usando o `clientCredentials` comportamento **cuidado:**  Windows Communication Foundation (WCF) não oferece suporte para enviar um resumo de senha ou derivação de chaves usando a senha e essas chaves para segurança de mensagem. Portanto, o WCF impõe que o exchange esteja protegido ao usar as credenciais de nome de usuário. Esse modo exige que o certificado de serviço seja especificado no lado cliente usando `clientCredential` comportamento e `serviceCertificate`. <br /><br /> -Certificado: Isso permite que o serviço exigir que o cliente seja autenticado usando um certificado. A credencial do cliente nesse caso, deve ser especificado usando o `clientCredentials` comportamento. A credencial de serviço neste caso deve ser especificado usando o `clientCredentials` comportamento especificando o `serviceCertificate`.<br />-CardSpace: Isso permite que o serviço exigir que o cliente seja autenticado usando um CardSpace. O `serviceCertificate` devem ser provisionados no `clientCredential` comportamento.<br /><br /> O valor padrão é `Windows`. Esse atributo é do tipo <xref:System.ServiceModel.MessageCredentialType>.|

### <a name="child-elements"></a>Elementos filho

Nenhum

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[\<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|Define as configurações de segurança para uma associação.|

## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [Filas no WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Associações](../../../../../docs/framework/wcf/bindings.md)
- [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Usando associações para configurar serviços e clientes](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../../../docs/framework/misc/binding.md)
