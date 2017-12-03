---
title: "Integração com visão geral de aplicativos COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6ae704ad9542c162b1c37f3eb9edf31f864cd42e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="integrating-with-com-applications-overview"></a><span data-ttu-id="191d6-102">Integração com visão geral de aplicativos COM</span><span class="sxs-lookup"><span data-stu-id="191d6-102">Integrating with COM Applications Overview</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="191d6-103">oferece ao desenvolvedor de código gerenciado com um ambiente rico para criar aplicativos conectados.</span><span class="sxs-lookup"><span data-stu-id="191d6-103"> provides the managed code developer with a rich environment for creating connected applications.</span></span> <span data-ttu-id="191d6-104">No entanto, se você tem um investimento significativo em código não gerenciado COM base em e não deseja migrar, você pode ainda integrar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços da Web diretamente no seu código existente usando o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker de serviço.</span><span class="sxs-lookup"><span data-stu-id="191d6-104">However, if you have a substantial investment in unmanaged COM-based code and do not want to migrate, you can still integrate [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web services directly into your existing code by using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker.</span></span> <span data-ttu-id="191d6-105">O moniker de serviço pode ser usado em ambientes de desenvolvimento todo com base no intervalo de COM, como Office VBA, Visual Basic 6.0 ou Visual C++ 6.0.</span><span class="sxs-lookup"><span data-stu-id="191d6-105">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="191d6-106">O moniker de serviço usa um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] canal de comunicação para todas as comunicações.</span><span class="sxs-lookup"><span data-stu-id="191d6-106">The service moniker uses a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] communication channel for all communication.</span></span> <span data-ttu-id="191d6-107">Os mecanismos de segurança e identidade para esse canal diferem daqueles usados no padrão proxies COM e DCOM.</span><span class="sxs-lookup"><span data-stu-id="191d6-107">The security and identity mechanisms for that channel differ from those used in standard COM and DCOM proxies.</span></span> <span data-ttu-id="191d6-108">Além disso, como o moniker de serviço usa um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] canal de comunicação, o período de tempo limite padrão é um minuto para todas as chamadas.</span><span class="sxs-lookup"><span data-stu-id="191d6-108">In addition, because the service moniker uses a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] communication channel the default timeout period is one minute for all calls.</span></span>  
  
 <span data-ttu-id="191d6-109">O moniker de serviço é usado com o `GetObject` função para fornecer o desenvolvedor não gerenciado com uma abordagem fortemente tipada COM específicas para chamar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços Web.</span><span class="sxs-lookup"><span data-stu-id="191d6-109">The service moniker is used with the `GetObject` function to provide the unmanaged developer with a strongly-typed, COM-specific approach for calling [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web services.</span></span> <span data-ttu-id="191d6-110">Isso requer uma definição de local, COM visível do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web contrato de serviço e a associação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="191d6-110">This requires a local, COM-visible definition of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web service contract and the binding that is to be used.</span></span> <span data-ttu-id="191d6-111">Assim como outros [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clientes, o moniker de serviço devem criar um canal inserido para o serviço, embora essa construção de canal ocorre de forma transparente para o programador COM na primeira chamada do método.</span><span class="sxs-lookup"><span data-stu-id="191d6-111">Like other [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients, the service moniker must construct a typed channel to the service, though this channel construction occurs transparently to the COM programmer on the first method call.</span></span>  
  
 <span data-ttu-id="191d6-112">Em comum com outros [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clientes, ao usar o moniker o aplicativos especificam o endereço, associação e contrato para se comunicar com um serviço.</span><span class="sxs-lookup"><span data-stu-id="191d6-112">In common with other [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients, when using the moniker, applications specify the address, binding and contract to communicate with a service.</span></span> <span data-ttu-id="191d6-113">O contrato pode ser especificado em uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="191d6-113">The contract can be specified in one of the following ways:</span></span>  
  
-   <span data-ttu-id="191d6-114">Contrato com tipo – o contrato é registrado como um tipo visível COM no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="191d6-114">Typed contract – the contract is registered as a COM visible type on the client machine.</span></span>  
  
-   <span data-ttu-id="191d6-115">Contrato WSDL – o contrato é fornecido na forma de um documento WSDL.</span><span class="sxs-lookup"><span data-stu-id="191d6-115">WSDL contract – the contract is supplied in the form of a WSDL document.</span></span>  
  
-   <span data-ttu-id="191d6-116">Contrato MEX – o contrato é recuperado em tempo de execução de um ponto de extremidade de troca de metadados (MEX).</span><span class="sxs-lookup"><span data-stu-id="191d6-116">MEX contract – the contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="parameters-supported-by-the-service-moniker"></a><span data-ttu-id="191d6-117">Parâmetros compatíveis com o Moniker de serviço</span><span class="sxs-lookup"><span data-stu-id="191d6-117">Parameters Supported by the Service Moniker</span></span>  
 <span data-ttu-id="191d6-118">A tabela a seguir mostra os parâmetros que são suportados pelo moniker de serviço.</span><span class="sxs-lookup"><span data-stu-id="191d6-118">The following table shows the parameters that are supported by the service moniker.</span></span>  
  
|<span data-ttu-id="191d6-119">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="191d6-119">Parameter</span></span>|<span data-ttu-id="191d6-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="191d6-120">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="191d6-121">Local da URL do serviço.</span><span class="sxs-lookup"><span data-stu-id="191d6-121">URL location of the service.</span></span>|  
|`binding`|<span data-ttu-id="191d6-122">Associação de nome da seção de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="191d6-122">Binding section name from the application configuration.</span></span>|  
|`bindingConfiguration`|<span data-ttu-id="191d6-123">Instância nomeada de associação de dentro da seção de ligação nomeada.</span><span class="sxs-lookup"><span data-stu-id="191d6-123">Named binding instance from within the named binding section.</span></span>|  
|`contract`|<span data-ttu-id="191d6-124">Identificador de interface (IID) que representa o contrato de serviço ou o nome do contrato (de MEX).</span><span class="sxs-lookup"><span data-stu-id="191d6-124">Interface identifier (IID) that represents the service contract or the contract name (from MEX).</span></span>|  
|`wsdl`|<span data-ttu-id="191d6-125">Documento WSDL que fornece uma maneira alternativa de definição de contrato.</span><span class="sxs-lookup"><span data-stu-id="191d6-125">WSDL document that provides an alternative form of contract definition.</span></span>|  
|`spnIdentity`|<span data-ttu-id="191d6-126">Identidade do servidor (SPN) nome da entidade a ser usado para se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="191d6-126">Server principal name (SPN) identity to be used to communicate with the service.</span></span>|  
|`upnIdentity`|<span data-ttu-id="191d6-127">Identidade de nome principal (UPN) do usuário a ser usado para se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="191d6-127">User principal name (UPN) identity to be used to communicate with the service.</span></span>|  
|`dnsIdentity`|<span data-ttu-id="191d6-128">Identidade do DNS a ser usado para se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="191d6-128">DNS identity to be used to communicate with the service.</span></span>|  
|`mexAddress`|<span data-ttu-id="191d6-129">Local da URL do ponto de extremidade do serviço de troca de metadados (MEX).</span><span class="sxs-lookup"><span data-stu-id="191d6-129">URL location of the Metadata Exchange (MEX) endpoint of the service.</span></span>|  
|`mexBinding`|<span data-ttu-id="191d6-130">Associação de nome de seção de configuração do aplicativo para se conectar com o ponto de extremidade MEX.</span><span class="sxs-lookup"><span data-stu-id="191d6-130">Binding section name from the application configuration to connect with the MEX endpoint.</span></span>|  
|`mexBindingConfiguration`|<span data-ttu-id="191d6-131">Instância nomeada de associação de dentro da seção de ligação nomeada para se conectar com o ponto de extremidade MEX.</span><span class="sxs-lookup"><span data-stu-id="191d6-131">Named binding instance from within the named binding section to connect with the MEX endpoint.</span></span>|  
|`bindingNamespace`|<span data-ttu-id="191d6-132">Namespace do nome da seção de associação do MEX. recuperados</span><span class="sxs-lookup"><span data-stu-id="191d6-132">Namespace of the binding section name from the retrieved MEX.</span></span>|  
|`contractNamespace`|<span data-ttu-id="191d6-133">Namespace do contrato do MEX. recuperados</span><span class="sxs-lookup"><span data-stu-id="191d6-133">Namespace of the contract from the retrieved MEX.</span></span>|  
|`mexSpnIdentity`|<span data-ttu-id="191d6-134">Identidade do servidor (SPN) nome da entidade a ser usado para se comunicar com o ponto de extremidade MEX.</span><span class="sxs-lookup"><span data-stu-id="191d6-134">Server principal name (SPN) identity to be used to communicate with the MEX endpoint.</span></span>|  
|`mexUpnIdentity`|<span data-ttu-id="191d6-135">Identidade de nome principal (UPN) do usuário a ser usado para se comunicar com o ponto de extremidade MEX.</span><span class="sxs-lookup"><span data-stu-id="191d6-135">User principal name (UPN) identity to be used to communicate with the MEX endpoint.</span></span>|  
|`mexDnsIdentity`|<span data-ttu-id="191d6-136">Identidade do DNS a ser usado para se comunicar com o ponto de extremidade MEX.</span><span class="sxs-lookup"><span data-stu-id="191d6-136">DNS identity to be used to communicate with the MEX endpoint.</span></span>|  
|`serializer`|<span data-ttu-id="191d6-137">Especifique o uso do serializador de um "datacontract" ou "xml".</span><span class="sxs-lookup"><span data-stu-id="191d6-137">Specify the use of either the "xml" or "datacontract" serializer.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="191d6-138">Mesmo quando usado com clientes inteiramente baseados em COM, o moniker de serviço requer [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] e suporte do .NET Framework 2.0 para ser instalado no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="191d6-138">Even when used with entirely COM-based clients, the service moniker requires [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and the supporting .NET Framework 2.0 to be installed on the client computer.</span></span> <span data-ttu-id="191d6-139">Também é importante que os aplicativos cliente que usam o moniker de serviço carregar a versão apropriada do tempo de execução do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="191d6-139">It is also critical that client applications that use the service moniker load the appropriate version of the .NET Framework runtime.</span></span> <span data-ttu-id="191d6-140">Ao usar o moniker em aplicativos do Office, um arquivo de configuração pode ser necessário para garantir que a versão do framework correto seja carregada.</span><span class="sxs-lookup"><span data-stu-id="191d6-140">When using the moniker within Office applications, a configuration file may be required to ensure that the correct framework version is loaded.</span></span> <span data-ttu-id="191d6-141">Por exemplo, com o Excel, o texto a seguir deve ser colocado em um arquivo chamado Excel.exe.config no mesmo diretório que o arquivo Excel.exe:</span><span class="sxs-lookup"><span data-stu-id="191d6-141">For example, with Excel, the following text should be placed in a file called Excel.exe.config in the same directory as the Excel.exe file:</span></span>  
>   
>  `<?xml version="1.0" encoding="utf-8"?>`  
>   
>  <span data-ttu-id="191d6-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span><span class="sxs-lookup"><span data-stu-id="191d6-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span></span>  
>   
>  `<startup>`  
>   
>  `<requiredRuntime version="v2.0.50727" />`  
>   
>  `</startup>`  
>   
>  `</configuration>`  
  
## <a name="see-also"></a><span data-ttu-id="191d6-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="191d6-143">See Also</span></span>  
 [<span data-ttu-id="191d6-144">Como: registrar e configurar um Moniker de serviço</span><span class="sxs-lookup"><span data-stu-id="191d6-144">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
