---
title: ServiceAppDomain
ms.date: 03/30/2017
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
ms.openlocfilehash: aef0a0da9d107b92d9d3017968d5554205a6fd71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
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
