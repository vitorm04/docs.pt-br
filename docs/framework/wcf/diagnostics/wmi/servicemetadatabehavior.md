---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 1d99af064205447c2f11f6f19258551c1e88d386
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976125"
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
