---
title: Classe de canal
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: f60a3946617b0994db1ba9e9ddf43be863be81f9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767442"
---
# <a name="channel-class"></a><span data-ttu-id="7c30b-102">Classe de canal</span><span class="sxs-lookup"><span data-stu-id="7c30b-102">Channel class</span></span>
<span data-ttu-id="7c30b-103">Canal</span><span class="sxs-lookup"><span data-stu-id="7c30b-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c30b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7c30b-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="7c30b-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="7c30b-105">Methods</span></span>  
 <span data-ttu-id="7c30b-106">A classe de canal não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="7c30b-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7c30b-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="7c30b-107">Properties</span></span>  
 <span data-ttu-id="7c30b-108">A classe de canal tem as propriedades a seguir.</span><span class="sxs-lookup"><span data-stu-id="7c30b-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="7c30b-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="7c30b-109">LocalAddress</span></span>  
 <span data-ttu-id="7c30b-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7c30b-110">Data type: string</span></span>  
  
 <span data-ttu-id="7c30b-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7c30b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7c30b-112">O ponto de extremidade local para o canal.</span><span class="sxs-lookup"><span data-stu-id="7c30b-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="7c30b-113">ref</span><span class="sxs-lookup"><span data-stu-id="7c30b-113">ref</span></span>  
 <span data-ttu-id="7c30b-114">Tipo de dados: Ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="7c30b-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="7c30b-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7c30b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7c30b-116">Uma referência para o ponto de extremidade do canal se conecta ao.</span><span class="sxs-lookup"><span data-stu-id="7c30b-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="7c30b-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="7c30b-117">RemoteAddress</span></span>  
 <span data-ttu-id="7c30b-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7c30b-118">Data type: string</span></span>  
  
 <span data-ttu-id="7c30b-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7c30b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7c30b-120">O endereço remoto associado ao canal.</span><span class="sxs-lookup"><span data-stu-id="7c30b-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="7c30b-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="7c30b-121">SessionId</span></span>  
 <span data-ttu-id="7c30b-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7c30b-122">Data type: string</span></span>  
  
 <span data-ttu-id="7c30b-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7c30b-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7c30b-124">A sessão atual de Id, se houver.</span><span class="sxs-lookup"><span data-stu-id="7c30b-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="7c30b-125">Tipo</span><span class="sxs-lookup"><span data-stu-id="7c30b-125">Type</span></span>  
 <span data-ttu-id="7c30b-126">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7c30b-126">Data type: string</span></span>  
  
 <span data-ttu-id="7c30b-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7c30b-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7c30b-128">O tipo de canal.</span><span class="sxs-lookup"><span data-stu-id="7c30b-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c30b-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7c30b-129">Requirements</span></span>  
  
|<span data-ttu-id="7c30b-130">MOF</span><span class="sxs-lookup"><span data-stu-id="7c30b-130">MOF</span></span>|<span data-ttu-id="7c30b-131">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="7c30b-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7c30b-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="7c30b-132">Namespace</span></span>|<span data-ttu-id="7c30b-133">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7c30b-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7c30b-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c30b-134">See also</span></span>

- <xref:System.ServiceModel.Channels.ChannelBase>
