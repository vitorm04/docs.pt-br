---
title: Classe de canal
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: 108d5f8e3cd092863dbd48e2bb9d180798b091a4
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50047365"
---
# <a name="channel-class"></a><span data-ttu-id="8ff64-102">Classe de canal</span><span class="sxs-lookup"><span data-stu-id="8ff64-102">Channel class</span></span>
<span data-ttu-id="8ff64-103">Canal</span><span class="sxs-lookup"><span data-stu-id="8ff64-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ff64-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8ff64-104">Syntax</span></span>  
  
```csharp
class Channel  
{  
  string LocalAddress;  
  Endpoint ref;  
  string RemoteAddress;  
  string SessionId;  
  string Type;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8ff64-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="8ff64-105">Methods</span></span>  
 <span data-ttu-id="8ff64-106">A classe de canal não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="8ff64-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8ff64-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="8ff64-107">Properties</span></span>  
 <span data-ttu-id="8ff64-108">A classe de canal tem as propriedades a seguir.</span><span class="sxs-lookup"><span data-stu-id="8ff64-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="8ff64-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="8ff64-109">LocalAddress</span></span>  
 <span data-ttu-id="8ff64-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8ff64-110">Data type: string</span></span>  
  
 <span data-ttu-id="8ff64-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="8ff64-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8ff64-112">O ponto de extremidade local para o canal.</span><span class="sxs-lookup"><span data-stu-id="8ff64-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="8ff64-113">ref</span><span class="sxs-lookup"><span data-stu-id="8ff64-113">ref</span></span>  
 <span data-ttu-id="8ff64-114">Tipo de dados: ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="8ff64-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="8ff64-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="8ff64-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8ff64-116">Uma referência para o ponto de extremidade do canal se conecta ao.</span><span class="sxs-lookup"><span data-stu-id="8ff64-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="8ff64-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="8ff64-117">RemoteAddress</span></span>  
 <span data-ttu-id="8ff64-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8ff64-118">Data type: string</span></span>  
  
 <span data-ttu-id="8ff64-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="8ff64-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8ff64-120">O endereço remoto associado ao canal.</span><span class="sxs-lookup"><span data-stu-id="8ff64-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="8ff64-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="8ff64-121">SessionId</span></span>  
 <span data-ttu-id="8ff64-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8ff64-122">Data type: string</span></span>  
  
 <span data-ttu-id="8ff64-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="8ff64-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8ff64-124">A sessão atual de Id, se houver.</span><span class="sxs-lookup"><span data-stu-id="8ff64-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="8ff64-125">Tipo</span><span class="sxs-lookup"><span data-stu-id="8ff64-125">Type</span></span>  
 <span data-ttu-id="8ff64-126">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8ff64-126">Data type: string</span></span>  
  
 <span data-ttu-id="8ff64-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="8ff64-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8ff64-128">O tipo de canal.</span><span class="sxs-lookup"><span data-stu-id="8ff64-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ff64-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8ff64-129">Requirements</span></span>  
  
|<span data-ttu-id="8ff64-130">MOF</span><span class="sxs-lookup"><span data-stu-id="8ff64-130">MOF</span></span>|<span data-ttu-id="8ff64-131">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="8ff64-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8ff64-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="8ff64-132">Namespace</span></span>|<span data-ttu-id="8ff64-133">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8ff64-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8ff64-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ff64-134">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelBase>
