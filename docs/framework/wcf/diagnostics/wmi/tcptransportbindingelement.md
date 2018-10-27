---
title: TcpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
ms.openlocfilehash: 04326484bbf1f07c66ad8fb401642880f9ba8c6e
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50033708"
---
# <a name="tcptransportbindingelement"></a><span data-ttu-id="ccf50-102">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="ccf50-102">TcpTransportBindingElement</span></span>
<span data-ttu-id="ccf50-103">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="ccf50-103">TcpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccf50-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ccf50-104">Syntax</span></span>  
  
```csharp
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ccf50-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="ccf50-105">Methods</span></span>  
 <span data-ttu-id="ccf50-106">A classe TcpTransportBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="ccf50-106">The TcpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ccf50-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="ccf50-107">Properties</span></span>  
 <span data-ttu-id="ccf50-108">A classe TcpTransportBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="ccf50-108">The TcpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="connectionpoolsettings"></a><span data-ttu-id="ccf50-109">connectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="ccf50-109">ConnectionPoolSettings</span></span>  
 <span data-ttu-id="ccf50-110">Tipo de dados: TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="ccf50-110">Data type: TcpConnectionPoolSettings</span></span>  
  
 <span data-ttu-id="ccf50-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="ccf50-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ccf50-112">As configurações do pool de conexão.</span><span class="sxs-lookup"><span data-stu-id="ccf50-112">The connection pool settings.</span></span>  
  
### <a name="listenbacklog"></a><span data-ttu-id="ccf50-113">listenBacklog</span><span class="sxs-lookup"><span data-stu-id="ccf50-113">ListenBacklog</span></span>  
 <span data-ttu-id="ccf50-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="ccf50-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="ccf50-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="ccf50-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ccf50-116">O número máximo de solicitações de conexão em fila que podem estar pendentes.</span><span class="sxs-lookup"><span data-stu-id="ccf50-116">The maximum number of queued connection requests that can be pending.</span></span>  
  
### <a name="portsharingenabled"></a><span data-ttu-id="ccf50-117">portSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="ccf50-117">PortSharingEnabled</span></span>  
 <span data-ttu-id="ccf50-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="ccf50-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="ccf50-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="ccf50-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ccf50-120">Um valor booliano que especifica se o compartilhamento de porta TCP está habilitado para esta conexão.</span><span class="sxs-lookup"><span data-stu-id="ccf50-120">A boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span>  
  
### <a name="teredoenabled"></a><span data-ttu-id="ccf50-121">teredoEnabled</span><span class="sxs-lookup"><span data-stu-id="ccf50-121">TeredoEnabled</span></span>  
 <span data-ttu-id="ccf50-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="ccf50-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="ccf50-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="ccf50-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ccf50-124">Um valor booliano que especifica se Teredo (uma tecnologia para endereçar cliente que estão atrás de firewalls) está habilitado.</span><span class="sxs-lookup"><span data-stu-id="ccf50-124">A boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccf50-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ccf50-125">Requirements</span></span>  
  
|<span data-ttu-id="ccf50-126">MOF</span><span class="sxs-lookup"><span data-stu-id="ccf50-126">MOF</span></span>|<span data-ttu-id="ccf50-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ccf50-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ccf50-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="ccf50-128">Namespace</span></span>|<span data-ttu-id="ccf50-129">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ccf50-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ccf50-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ccf50-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
