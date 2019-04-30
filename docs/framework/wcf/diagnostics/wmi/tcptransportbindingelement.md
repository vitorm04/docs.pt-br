---
title: TcpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
ms.openlocfilehash: 6d2717bc2d1d14e369af2b9c5a8c0affb67501d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956540"
---
# <a name="tcptransportbindingelement"></a><span data-ttu-id="900d8-102">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="900d8-102">TcpTransportBindingElement</span></span>
<span data-ttu-id="900d8-103">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="900d8-103">TcpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="900d8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="900d8-104">Syntax</span></span>  
  
```csharp
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="900d8-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="900d8-105">Methods</span></span>  
 <span data-ttu-id="900d8-106">A classe TcpTransportBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="900d8-106">The TcpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="900d8-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="900d8-107">Properties</span></span>  
 <span data-ttu-id="900d8-108">A classe TcpTransportBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="900d8-108">The TcpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="connectionpoolsettings"></a><span data-ttu-id="900d8-109">ConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="900d8-109">ConnectionPoolSettings</span></span>  
 <span data-ttu-id="900d8-110">Tipo de dados: TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="900d8-110">Data type: TcpConnectionPoolSettings</span></span>  
  
 <span data-ttu-id="900d8-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="900d8-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="900d8-112">As configurações do pool de conexão.</span><span class="sxs-lookup"><span data-stu-id="900d8-112">The connection pool settings.</span></span>  
  
### <a name="listenbacklog"></a><span data-ttu-id="900d8-113">listenBacklog</span><span class="sxs-lookup"><span data-stu-id="900d8-113">ListenBacklog</span></span>  
 <span data-ttu-id="900d8-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="900d8-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="900d8-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="900d8-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="900d8-116">O número máximo de solicitações de conexão em fila que podem estar pendentes.</span><span class="sxs-lookup"><span data-stu-id="900d8-116">The maximum number of queued connection requests that can be pending.</span></span>  
  
### <a name="portsharingenabled"></a><span data-ttu-id="900d8-117">PortSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="900d8-117">PortSharingEnabled</span></span>  
 <span data-ttu-id="900d8-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="900d8-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="900d8-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="900d8-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="900d8-120">Um valor booliano que especifica se o compartilhamento de porta TCP está habilitado para esta conexão.</span><span class="sxs-lookup"><span data-stu-id="900d8-120">A boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span>  
  
### <a name="teredoenabled"></a><span data-ttu-id="900d8-121">TeredoEnabled</span><span class="sxs-lookup"><span data-stu-id="900d8-121">TeredoEnabled</span></span>  
 <span data-ttu-id="900d8-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="900d8-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="900d8-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="900d8-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="900d8-124">Um valor booliano que especifica se Teredo (uma tecnologia para endereçar cliente que estão atrás de firewalls) está habilitado.</span><span class="sxs-lookup"><span data-stu-id="900d8-124">A boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="900d8-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="900d8-125">Requirements</span></span>  
  
|<span data-ttu-id="900d8-126">MOF</span><span class="sxs-lookup"><span data-stu-id="900d8-126">MOF</span></span>|<span data-ttu-id="900d8-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="900d8-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="900d8-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="900d8-128">Namespace</span></span>|<span data-ttu-id="900d8-129">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="900d8-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="900d8-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="900d8-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
