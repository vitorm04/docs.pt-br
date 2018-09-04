---
title: Configurando WCF Data Services
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 05006ff3-02dc-410e-831e-54ec3e7e24ef
ms.openlocfilehash: c0c9010a71877d2c9757a2c9cf2d5c1fec8aedf7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481264"
---
# <a name="defining-wcf-data-services"></a><span data-ttu-id="bb4a4-102">Configurando WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="bb4a4-102">Defining WCF Data Services</span></span>

<span data-ttu-id="bb4a4-103">Esta seção descreve como criar e configurar o WCF Data Services para expor dados como um [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed.</span><span class="sxs-lookup"><span data-stu-id="bb4a4-103">This section describes how to create and configure WCF Data Services to expose data as an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed.</span></span> <span data-ttu-id="bb4a4-104">Para obter mais informações sobre as etapas básicas necessárias para criar um serviço de dados, consulte [expor seus dados como um serviço](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="bb4a4-104">For more information about the basic steps required to create a data service, see [Exposing Your Data as a Service](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="bb4a4-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="bb4a4-105">In This Section</span></span>

 [<span data-ttu-id="bb4a4-106">Configurando o serviço de dados</span><span class="sxs-lookup"><span data-stu-id="bb4a4-106">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)

 <span data-ttu-id="bb4a4-107">Descreve as opções de configuração do serviço de dados fornecidas pelo WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="bb4a4-107">Describes the data service configuration options provided by WCF Data Services.</span></span>

 [<span data-ttu-id="bb4a4-108">Provedores de Serviços de Dados</span><span class="sxs-lookup"><span data-stu-id="bb4a4-108">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)

 <span data-ttu-id="bb4a4-109">Descreve os modelos de provedor para expor dados como um serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="bb4a4-109">Describes the provider models for exposing data as a data service.</span></span>

 [<span data-ttu-id="bb4a4-110">Operações de serviço</span><span class="sxs-lookup"><span data-stu-id="bb4a4-110">Service Operations</span></span>](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)

 <span data-ttu-id="bb4a4-111">Descreve como definir as operações de serviço que expõem métodos no servidor.</span><span class="sxs-lookup"><span data-stu-id="bb4a4-111">Describes how to define service operations that expose methods on the server.</span></span>

 [<span data-ttu-id="bb4a4-112">Personalização de feed</span><span class="sxs-lookup"><span data-stu-id="bb4a4-112">Feed Customization</span></span>](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md)

 <span data-ttu-id="bb4a4-113">Descreve como criar um mapeamento entre entidades no modelo de dados definido pelo provedor de serviços de dados e elementos no feed de dados.</span><span class="sxs-lookup"><span data-stu-id="bb4a4-113">Describes how to create a mapping between entities in the data model defined by the data service provider and elements in the data feed.</span></span>

 [<span data-ttu-id="bb4a4-114">Interceptadores</span><span class="sxs-lookup"><span data-stu-id="bb4a4-114">Interceptors</span></span>](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)

 <span data-ttu-id="bb4a4-115">Descreve como definir métodos de interceptador para executar lógica de negócios personalizado em solicitações para o serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="bb4a4-115">Describes how to define interceptor methods to perform custom business logic on requests to the data service.</span></span>

 [<span data-ttu-id="bb4a4-116">Desenvolvendo e implantando o WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="bb4a4-116">Developing and Deploying WCF Data Services</span></span>](../../../../docs/framework/data/wcf/developing-and-deploying-wcf-data-services.md)

 <span data-ttu-id="bb4a4-117">Descreve como desenvolver e implantar um serviço de dados usando o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bb4a4-117">Describes how to develop and deploy a data service by using Visual Studio.</span></span>

 [<span data-ttu-id="bb4a4-118">Protegendo o WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="bb4a4-118">Securing WCF Data Services</span></span>](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)

 <span data-ttu-id="bb4a4-119">Descreve a autenticação e a autorização para o serviço de dados e outras considerações de segurança.</span><span class="sxs-lookup"><span data-stu-id="bb4a4-119">Describes authentication and authorization for the data service and other security considerations.</span></span>

 [<span data-ttu-id="bb4a4-120">Hospedagem o serviço de dados</span><span class="sxs-lookup"><span data-stu-id="bb4a4-120">Hosting the Data Service</span></span>](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)

 <span data-ttu-id="bb4a4-121">Descreve como selecionar um host para o serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="bb4a4-121">Describes how to select a host for your data service.</span></span>

 [<span data-ttu-id="bb4a4-122">Controle de versão de serviço de dados</span><span class="sxs-lookup"><span data-stu-id="bb4a4-122">Data Service Versioning</span></span>](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)

 <span data-ttu-id="bb4a4-123">Descreve como trabalhar com diferentes versões do OData.</span><span class="sxs-lookup"><span data-stu-id="bb4a4-123">Describes how to work with different versions of the OData.</span></span>

 [<span data-ttu-id="bb4a4-124">Detalhes de implementação do protocolo do WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="bb4a4-124">WCF Data Services Protocol Implementation Details</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-protocol-implementation-details.md)

 <span data-ttu-id="bb4a4-125">Descreve as funcionalidades opcionais do protocolo OData que não estejam atualmente implementadas pelo WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="bb4a4-125">Describes optional functionalities of the OData protocol that are not currently implemented by WCF Data Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="bb4a4-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb4a4-126">See Also</span></span>

- <span data-ttu-id="bb4a4-127">[WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="bb4a4-127">[WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)</span></span>
- [<span data-ttu-id="bb4a4-128">Acessando recursos do serviço de dados</span><span class="sxs-lookup"><span data-stu-id="bb4a4-128">Accessing Data Service Resources</span></span>](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)
- [<span data-ttu-id="bb4a4-129">Introdução</span><span class="sxs-lookup"><span data-stu-id="bb4a4-129">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
