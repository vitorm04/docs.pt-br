---
title: ServiceAppDomain
ms.date: 03/30/2017
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
ms.openlocfilehash: 05be495dbfe87e7dd14b0cfbb38b30c6f8278e6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61957067"
---
# <a name="serviceappdomain"></a>ServiceAppDomain
Mapeia um serviço para um domínio de aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe ServiceAppDomain não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe ServiceAppDomain tem as seguintes propriedades:  
  
### <a name="ref"></a>ref  
 Tipo de dados: Serviço  
Qualificadores: Chave  
  
 Tipo de acesso: Somente leitura  
  
 O serviço desse domínio de aplicativo.  
  
### <a name="ref"></a>ref  
 Tipo de dados: AppDomainInfo  
Qualificadores: Chave  
  
 Tipo de acesso: Somente leitura  
  
 Contém propriedades do domínio do aplicativo.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|
