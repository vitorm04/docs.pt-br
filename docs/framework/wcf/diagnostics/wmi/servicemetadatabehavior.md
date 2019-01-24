---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 76e28b18cd595a4a18f573dfe9539b646196c944
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720334"
---
# <a name="servicemetadatabehavior"></a>ServiceMetadataBehavior
ServiceMetadataBehavior  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
class ServiceMetadataBehavior : Behavior  
{  
  string ExternalMetadataLocation;  
  boolean HttpGetEnabled;  
  string HttpGetUrl;  
  boolean HttpsGetEnabled;  
  string HttpsGetUrl;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe ServiceMetadataBehavior não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe ServiceMetadataBehavior tem as seguintes propriedades:  
  
### <a name="externalmetadatalocation"></a>ExternalMetadataLocation  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 Define o local para o qual o serviço redireciona solicitações de metadados.  
  
### <a name="httpgetenabled"></a>HttpGetEnabled  
 Tipo de dados: boolean  
  
 Tipo de acesso: Somente leitura  
  
 Controla se o serviço publica seu WSDL no endereço controlado pela `HttpGetUrl` atributo.  
  
### <a name="httpgeturl"></a>HttpGetUrl  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 Define o local no qual o serviço WSDL é publicado para recuperação usando HTTP.  
  
### <a name="httpsgetenabled"></a>HttpsGetEnabled  
 Tipo de dados: boolean  
  
 Tipo de acesso: Somente leitura  
  
 Controla se o serviço publica seu WSDL via HTTPS no endereço controlado pela `HttpsGetUrl` atributo.  
  
### <a name="httpsgeturl"></a>HttpsGetUrl  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 Define o local no qual o serviço WSDL é publicado para recuperação usando HTTPS.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
