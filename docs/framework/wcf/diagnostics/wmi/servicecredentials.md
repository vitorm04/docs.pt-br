---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: 18100ac36b5116c2373171ff795fc23b75bbd6f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572114"
---
# <a name="servicecredentials"></a>ServiceCredentials
ServiceCredentials  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
class ServiceCredentials : Behavior  
{  
  string ClientCertificate;  
  string IssuedTokenAuthentication;  
  string Peer;  
  string SecureConversationAuthentication;  
  string ServiceCertificate;  
  string UserNameAuthentication;  
  string WindowsAuthentication;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe ServiceCredentials não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe ServiceCredentials tem as seguintes propriedades:  
  
### <a name="clientcertificate"></a>ClientCertificate  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 Os certificado de autenticação e provisionamento configurações do cliente para esse serviço.  
  
### <a name="issuedtokenauthentication"></a>IssuedTokenAuthentication  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 Atual emitido configurações de autenticação de token para este serviço.  
  
### <a name="peer"></a>Par  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 Configurações a serem usadas pelos pontos de extremidade de transporte de par de provisionamento e autenticação de credencial atual.  
  
### <a name="secureconversationauthentication"></a>SecureConversationAuthentication  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 Especifica as configurações atuais de conversa segura.  
  
### <a name="servicecertificate"></a>ServiceCertificate  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 O certificado associado a esse serviço.  
  
### <a name="usernameauthentication"></a>UserNameAuthentication  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 As configurações de nome de usuário e senha para esse serviço.  
  
### <a name="windowsauthentication"></a>WindowsAuthentication  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 As configurações de autenticação do Windows para este serviço.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Description.ServiceCredentials>
