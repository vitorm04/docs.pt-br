---
title: Classe de canal
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: f60a3946617b0994db1ba9e9ddf43be863be81f9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128837"
---
# <a name="channel-class"></a><span data-ttu-id="8b81f-102">Classe de canal</span><span class="sxs-lookup"><span data-stu-id="8b81f-102">Channel class</span></span>
<span data-ttu-id="8b81f-103">Canal</span><span class="sxs-lookup"><span data-stu-id="8b81f-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b81f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b81f-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="8b81f-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="8b81f-105">Methods</span></span>  
 <span data-ttu-id="8b81f-106">A classe de canal não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="8b81f-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8b81f-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="8b81f-107">Properties</span></span>  
 <span data-ttu-id="8b81f-108">A classe de canal tem as propriedades a seguir.</span><span class="sxs-lookup"><span data-stu-id="8b81f-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="8b81f-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="8b81f-109">LocalAddress</span></span>  
 <span data-ttu-id="8b81f-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8b81f-110">Data type: string</span></span>  
  
 <span data-ttu-id="8b81f-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="8b81f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8b81f-112">O ponto de extremidade local para o canal.</span><span class="sxs-lookup"><span data-stu-id="8b81f-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="8b81f-113">ref</span><span class="sxs-lookup"><span data-stu-id="8b81f-113">ref</span></span>  
 <span data-ttu-id="8b81f-114">Tipo de dados: Ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="8b81f-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="8b81f-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="8b81f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8b81f-116">Uma referência para o ponto de extremidade do canal se conecta ao.</span><span class="sxs-lookup"><span data-stu-id="8b81f-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="8b81f-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="8b81f-117">RemoteAddress</span></span>  
 <span data-ttu-id="8b81f-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8b81f-118">Data type: string</span></span>  
  
 <span data-ttu-id="8b81f-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="8b81f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8b81f-120">O endereço remoto associado ao canal.</span><span class="sxs-lookup"><span data-stu-id="8b81f-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="8b81f-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="8b81f-121">SessionId</span></span>  
 <span data-ttu-id="8b81f-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8b81f-122">Data type: string</span></span>  
  
 <span data-ttu-id="8b81f-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="8b81f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8b81f-124">A sessão atual de Id, se houver.</span><span class="sxs-lookup"><span data-stu-id="8b81f-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="8b81f-125">Tipo</span><span class="sxs-lookup"><span data-stu-id="8b81f-125">Type</span></span>  
 <span data-ttu-id="8b81f-126">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8b81f-126">Data type: string</span></span>  
  
 <span data-ttu-id="8b81f-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="8b81f-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8b81f-128">O tipo de canal.</span><span class="sxs-lookup"><span data-stu-id="8b81f-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b81f-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8b81f-129">Requirements</span></span>  
  
|<span data-ttu-id="8b81f-130">MOF</span><span class="sxs-lookup"><span data-stu-id="8b81f-130">MOF</span></span>|<span data-ttu-id="8b81f-131">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="8b81f-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8b81f-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="8b81f-132">Namespace</span></span>|<span data-ttu-id="8b81f-133">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8b81f-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8b81f-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b81f-134">See also</span></span>

- <xref:System.ServiceModel.Channels.ChannelBase>
