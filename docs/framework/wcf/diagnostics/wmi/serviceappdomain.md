---
title: ServiceAppDomain
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d948d1c77fc3f188694062ca9dcb3058f408c45
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="serviceappdomain"></a>ServiceAppDomain
Um serviço é mapeado para um domínio de aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe ServiceAppDomain não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe ServiceAppDomain tem as seguintes propriedades:  
  
### <a name="ref"></a>ref  
 Tipo de dados: serviço  
Qualificadores: chave  
  
 Tipo de acesso: somente leitura  
  
 O serviço desse domínio de aplicativo.  
  
### <a name="ref"></a>ref  
 Tipo de dados: AppDomainInfo  
Qualificadores: chave  
  
 Tipo de acesso: somente leitura  
  
 Contém propriedades do domínio do aplicativo.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|
