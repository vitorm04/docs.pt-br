---
title: TcpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
ms.openlocfilehash: 6d2717bc2d1d14e369af2b9c5a8c0affb67501d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124222"
---
# <a name="tcptransportbindingelement"></a><span data-ttu-id="8bf94-102">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="8bf94-102">TcpTransportBindingElement</span></span>
<span data-ttu-id="8bf94-103">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="8bf94-103">TcpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bf94-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8bf94-104">Syntax</span></span>  
  
```csharp
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8bf94-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="8bf94-105">Methods</span></span>  
 <span data-ttu-id="8bf94-106">A classe TcpTransportBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="8bf94-106">The TcpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8bf94-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="8bf94-107">Properties</span></span>  
 <span data-ttu-id="8bf94-108">A classe TcpTransportBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="8bf94-108">The TcpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="connectionpoolsettings"></a><span data-ttu-id="8bf94-109">ConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="8bf94-109">ConnectionPoolSettings</span></span>  
 <span data-ttu-id="8bf94-110">Tipo de dados: TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="8bf94-110">Data type: TcpConnectionPoolSettings</span></span>  
  
 <span data-ttu-id="8bf94-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="8bf94-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8bf94-112">As configurações do pool de conexão.</span><span class="sxs-lookup"><span data-stu-id="8bf94-112">The connection pool settings.</span></span>  
  
### <a name="listenbacklog"></a><span data-ttu-id="8bf94-113">listenBacklog</span><span class="sxs-lookup"><span data-stu-id="8bf94-113">ListenBacklog</span></span>  
 <span data-ttu-id="8bf94-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="8bf94-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="8bf94-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="8bf94-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8bf94-116">O número máximo de solicitações de conexão em fila que podem estar pendentes.</span><span class="sxs-lookup"><span data-stu-id="8bf94-116">The maximum number of queued connection requests that can be pending.</span></span>  
  
### <a name="portsharingenabled"></a><span data-ttu-id="8bf94-117">PortSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="8bf94-117">PortSharingEnabled</span></span>  
 <span data-ttu-id="8bf94-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="8bf94-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="8bf94-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="8bf94-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8bf94-120">Um valor booliano que especifica se o compartilhamento de porta TCP está habilitado para esta conexão.</span><span class="sxs-lookup"><span data-stu-id="8bf94-120">A boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span>  
  
### <a name="teredoenabled"></a><span data-ttu-id="8bf94-121">TeredoEnabled</span><span class="sxs-lookup"><span data-stu-id="8bf94-121">TeredoEnabled</span></span>  
 <span data-ttu-id="8bf94-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="8bf94-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="8bf94-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="8bf94-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8bf94-124">Um valor booliano que especifica se Teredo (uma tecnologia para endereçar cliente que estão atrás de firewalls) está habilitado.</span><span class="sxs-lookup"><span data-stu-id="8bf94-124">A boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bf94-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8bf94-125">Requirements</span></span>  
  
|<span data-ttu-id="8bf94-126">MOF</span><span class="sxs-lookup"><span data-stu-id="8bf94-126">MOF</span></span>|<span data-ttu-id="8bf94-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="8bf94-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8bf94-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="8bf94-128">Namespace</span></span>|<span data-ttu-id="8bf94-129">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8bf94-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8bf94-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8bf94-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
