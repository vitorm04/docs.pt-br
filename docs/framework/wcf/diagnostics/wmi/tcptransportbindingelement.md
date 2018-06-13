---
title: TcpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
ms.openlocfilehash: e64f689923d95546c8cecdf47c247faf79242ebf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485743"
---
# <a name="tcptransportbindingelement"></a><span data-ttu-id="b9b81-102">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="b9b81-102">TcpTransportBindingElement</span></span>
<span data-ttu-id="b9b81-103">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="b9b81-103">TcpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9b81-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b9b81-104">Syntax</span></span>  
  
```  
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b9b81-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="b9b81-105">Methods</span></span>  
 <span data-ttu-id="b9b81-106">A classe TcpTransportBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="b9b81-106">The TcpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b9b81-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b9b81-107">Properties</span></span>  
 <span data-ttu-id="b9b81-108">A classe TcpTransportBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="b9b81-108">The TcpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="connectionpoolsettings"></a><span data-ttu-id="b9b81-109">ConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="b9b81-109">ConnectionPoolSettings</span></span>  
 <span data-ttu-id="b9b81-110">Tipo de dados: TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="b9b81-110">Data type: TcpConnectionPoolSettings</span></span>  
  
 <span data-ttu-id="b9b81-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b9b81-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b9b81-112">As configurações de pool de conexão.</span><span class="sxs-lookup"><span data-stu-id="b9b81-112">The connection pool settings.</span></span>  
  
### <a name="listenbacklog"></a><span data-ttu-id="b9b81-113">ListenBacklog</span><span class="sxs-lookup"><span data-stu-id="b9b81-113">ListenBacklog</span></span>  
 <span data-ttu-id="b9b81-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="b9b81-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="b9b81-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b9b81-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b9b81-116">O número máximo de solicitações de conexão em fila que podem estar pendentes.</span><span class="sxs-lookup"><span data-stu-id="b9b81-116">The maximum number of queued connection requests that can be pending.</span></span>  
  
### <a name="portsharingenabled"></a><span data-ttu-id="b9b81-117">portSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="b9b81-117">PortSharingEnabled</span></span>  
 <span data-ttu-id="b9b81-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="b9b81-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="b9b81-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b9b81-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b9b81-120">Um valor booleano que especifica se o compartilhamento de porta TCP está habilitado para esta conexão.</span><span class="sxs-lookup"><span data-stu-id="b9b81-120">A boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span>  
  
### <a name="teredoenabled"></a><span data-ttu-id="b9b81-121">teredoEnabled</span><span class="sxs-lookup"><span data-stu-id="b9b81-121">TeredoEnabled</span></span>  
 <span data-ttu-id="b9b81-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="b9b81-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="b9b81-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b9b81-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b9b81-124">Um valor booleano que especifica se Teredo (uma tecnologia para endereçar cliente que estão atrás de firewalls) está habilitado.</span><span class="sxs-lookup"><span data-stu-id="b9b81-124">A boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9b81-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b9b81-125">Requirements</span></span>  
  
|<span data-ttu-id="b9b81-126">MOF</span><span class="sxs-lookup"><span data-stu-id="b9b81-126">MOF</span></span>|<span data-ttu-id="b9b81-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b9b81-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b9b81-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="b9b81-128">Namespace</span></span>|<span data-ttu-id="b9b81-129">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b9b81-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b9b81-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9b81-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
