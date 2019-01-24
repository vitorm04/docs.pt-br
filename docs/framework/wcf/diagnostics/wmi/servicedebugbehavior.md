---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: d6f0e4741aa10bff450a29cfd7a9e63e226c6495
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498876"
---
# <a name="servicedebugbehavior"></a>ServiceDebugBehavior
ServiceDebugBehavior  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
class ServiceDebugBehavior : Behavior  
{  
  boolean HttpHelpPageEnabled;  
  string HttpHelpPageUrl;  
  boolean HttpsHelpPageEnabled;  
  string HttpsHelpPageUrl;  
  boolean IncludeExceptionDetailInFaults;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe ServiceDebugBehavior não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe ServiceDebugBehavior tem as seguintes propriedades:  
  
### <a name="httphelppageenabled"></a>HttpHelpPageEnabled  
 Tipo de dados: boolean  
  
 Tipo de acesso: Somente leitura  
  
 Controla se o serviço publica seu WSDL no endereço controlado pela `HttpGetUrl` atributo.  
  
### <a name="httphelppageurl"></a>HttpHelpPageUrl  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 Define o local no qual o serviço WSDL é publicado para recuperação usando HTTP.  
  
### <a name="httpshelppageenabled"></a>HttpsHelpPageEnabled  
 Tipo de dados: boolean  
  
 Tipo de acesso: Somente leitura  
  
 Controla se o serviço publica seu WSDL via HTTPS no endereço controlado pela `HttpsGetUrl` atributo.  
  
### <a name="httpshelppageurl"></a>HttpsHelpPageUrl  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 Define o local no qual o serviço WSDL é publicado para recuperação usando HTTPS.  
  
### <a name="includeexceptiondetailinfaults"></a>IncludeExceptionDetailInFaults  
 Tipo de dados: boolean  
  
 Tipo de acesso: Somente leitura  
  
 Especifica se deve incluir informações de exceção gerenciada nos detalhes das falhas SOAP retornadas aos clientes para fins de depuração.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Description.ServiceDebugBehavior>
