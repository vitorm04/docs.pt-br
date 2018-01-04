---
title: ServiceDebugBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: af2dbd9e06876622b57379e17dbb4503cddbaac1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="servicedebugbehavior"></a>ServiceDebugBehavior
ServiceDebugBehavior  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
 A classe ServiceDebugBehavior não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe ServiceDebugBehavior tem as seguintes propriedades:  
  
### <a name="httphelppageenabled"></a>httpHelpPageEnabled  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Controla se o serviço publica seu WSDL no endereço controlado pelo `HttpGetUrl` atributo.  
  
### <a name="httphelppageurl"></a>httpHelpPageUrl  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Define o local no qual o serviço WSDL é publicado para recuperação usando HTTP.  
  
### <a name="httpshelppageenabled"></a>httpsHelpPageEnabled  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Controla se o serviço publica seu WSDL em HTTPS no endereço controlado pelo `HttpsGetUrl` atributo.  
  
### <a name="httpshelppageurl"></a>httpsHelpPageUrl  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Define o local no qual o serviço WSDL é publicado para recuperação usando HTTPS.  
  
### <a name="includeexceptiondetailinfaults"></a>includeExceptionDetailInFaults  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Especifica se deve incluir informações de exceção gerenciada no detalhe de falhas SOAP retornadas aos clientes para fins de depuração.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>
