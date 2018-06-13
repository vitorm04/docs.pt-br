---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: e96a732f8b3b4d78d597429905cc7dd290dcc606
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485994"
---
# <a name="servicemetadatabehavior"></a>ServiceMetadataBehavior
ServiceMetadataBehavior  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
 A classe de ServiceMetadataBehavior não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe de ServiceMetadataBehavior tem as seguintes propriedades:  
  
### <a name="externalmetadatalocation"></a>externalMetadataLocation  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Define o local para o qual o serviço redireciona solicitações de metadados.  
  
### <a name="httpgetenabled"></a>httpGetEnabled  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Controla se o serviço publica seu WSDL no endereço controlado pelo `HttpGetUrl` atributo.  
  
### <a name="httpgeturl"></a>httpGetUrl  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Define o local no qual o serviço WSDL é publicado para recuperação usando HTTP.  
  
### <a name="httpsgetenabled"></a>httpsGetEnabled  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Controla se o serviço publica seu WSDL em HTTPS no endereço controlado pelo `HttpsGetUrl` atributo.  
  
### <a name="httpsgeturl"></a>httpsGetUrl  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Define o local no qual o serviço WSDL é publicado para recuperação usando HTTPS.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
