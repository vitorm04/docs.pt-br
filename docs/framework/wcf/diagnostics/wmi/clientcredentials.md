---
title: ClientCredentials
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55f7ef12f67bd719f72f158a1fca6f120b4f448a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="clientcredentials"></a>ClientCredentials
ClientCredentials  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
 A classe ClientCredentials não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe ClientCredentials tem as seguintes propriedades:  
  
### <a name="clientcertificate"></a>ClientCertificate  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O certificado x. 509 o cliente usa para autenticar no serviço.  
  
### <a name="httpdigest"></a>HttpDigest  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 A credencial resumida Http.  
  
### <a name="issuedtoken"></a>IssuedToken  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O endereço do ponto de extremidade e a associação usada para entrar em contato com o serviço de token de segurança local.  
  
### <a name="peer"></a>ponto a ponto  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 As credenciais que o nó par usa para se autenticar em outros nós da malha.  
  
### <a name="servicecertificate"></a>ServiceCertificate  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Certificado de x. 509 do serviço.  
  
### <a name="supportinteractive"></a>SupportInteractive  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Um valor booleano que especifica se a credencial oferece suporte à negociação interativa.  
  
### <a name="username"></a>UserName  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O nome de usuário e a senha que o cliente usa para se autenticar para o serviço.  
  
### <a name="windows"></a>Windows  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 As credenciais do windows a cliente usa para se autenticar para o serviço.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Description.ClientCredentials>
