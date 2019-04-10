---
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: c3adc675bb6c1e9011459a88fd7dc8e8cf63a880
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226580"
---
# <a name="clientcredentials"></a>ClientCredentials
ClientCredentials  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
class ClientCredentials : Behavior  
{  
  string ClientCertificate;  
  string HttpDigest;  
  string IssuedToken;  
  string Peer;  
  string ServiceCertificate;  
  boolean SupportInteractive;  
  string UserName;  
  string Windows;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe ClientCredentials não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe ClientCredentials tem as seguintes propriedades:  
  
### <a name="clientcertificate"></a>ClientCertificate  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 O certificado x. 509 o cliente usa para se autenticar no serviço.  
  
### <a name="httpdigest"></a>HttpDigest  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 A credencial resumida Http atual.  
  
### <a name="issuedtoken"></a>IssuedToken  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 O endereço de ponto de extremidade e associação usado para contatar o serviço de token de segurança local.  
  
### <a name="peer"></a>Par  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 As credenciais que o nó par usa para se autenticar em outros nós na malha.  
  
### <a name="servicecertificate"></a>ServiceCertificate  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 O certificado do serviço x. 509.  
  
### <a name="supportinteractive"></a>SupportInteractive  
 Tipo de dados: boolean  
  
 Tipo de acesso: Somente leitura  
  
 Um valor booliano que especifica se a credencial dá suporte à negociação interativa.  
  
### <a name="username"></a>UserName  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 O nome de usuário e a senha que o cliente usa para autenticar-se com o serviço.  
  
### <a name="windows"></a>Windows  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 O cliente usa para se autenticar para o serviço de credenciais do windows.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Description.ClientCredentials>
