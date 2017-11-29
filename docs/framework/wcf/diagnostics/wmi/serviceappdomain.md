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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 36048f56c3b54447a112e6f0a457624062ce965a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="serviceappdomain"></a><span data-ttu-id="6fcfe-102">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="6fcfe-102">ServiceAppDomain</span></span>
<span data-ttu-id="6fcfe-103">Um serviço é mapeado para um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6fcfe-103">Maps a service to an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fcfe-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6fcfe-104">Syntax</span></span>  
  
```  
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6fcfe-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="6fcfe-105">Methods</span></span>  
 <span data-ttu-id="6fcfe-106">A classe ServiceAppDomain não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="6fcfe-106">The ServiceAppDomain class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6fcfe-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="6fcfe-107">Properties</span></span>  
 <span data-ttu-id="6fcfe-108">A classe ServiceAppDomain tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="6fcfe-108">The ServiceAppDomain class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="6fcfe-109">ref</span><span class="sxs-lookup"><span data-stu-id="6fcfe-109">ref</span></span>  
 <span data-ttu-id="6fcfe-110">Tipo de dados: serviço</span><span class="sxs-lookup"><span data-stu-id="6fcfe-110">Data type: Service</span></span>  
<span data-ttu-id="6fcfe-111">Qualificadores: chave</span><span class="sxs-lookup"><span data-stu-id="6fcfe-111">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="6fcfe-112">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="6fcfe-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6fcfe-113">O serviço desse domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6fcfe-113">The service of this application domain.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="6fcfe-114">ref</span><span class="sxs-lookup"><span data-stu-id="6fcfe-114">ref</span></span>  
 <span data-ttu-id="6fcfe-115">Tipo de dados: AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="6fcfe-115">Data type: AppDomainInfo</span></span>  
<span data-ttu-id="6fcfe-116">Qualificadores: chave</span><span class="sxs-lookup"><span data-stu-id="6fcfe-116">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="6fcfe-117">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="6fcfe-117">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6fcfe-118">Contém propriedades do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6fcfe-118">Contains properties of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fcfe-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6fcfe-119">Requirements</span></span>  
  
|<span data-ttu-id="6fcfe-120">MOF</span><span class="sxs-lookup"><span data-stu-id="6fcfe-120">MOF</span></span>|<span data-ttu-id="6fcfe-121">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="6fcfe-121">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6fcfe-122">Namespace</span><span class="sxs-lookup"><span data-stu-id="6fcfe-122">Namespace</span></span>|<span data-ttu-id="6fcfe-123">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6fcfe-123">Defined in root\ServiceModel</span></span>|
