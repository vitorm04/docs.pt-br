---
title: "Guia de Início Rápido (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a5223f9b6e7854ec6575e8673bb874a1b9b60df7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="f7ed5-102">Guia de Início Rápido (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="f7ed5-102">Quickstart (WCF Data Services)</span></span>
<span data-ttu-id="f7ed5-103">Este guia de início rápido ajuda você a se familiarizar com [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] e [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] por meio de uma série de tarefas que oferecem suporte os tópicos [Introdução](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="f7ed5-103">This quickstart helps you become familiar with [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] and the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] through a series of tasks that support the topics in [Getting Started](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md).</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="f7ed5-104">O que você aprenderá</span><span class="sxs-lookup"><span data-stu-id="f7ed5-104">What You Will Learn</span></span>  
 <span data-ttu-id="f7ed5-105">A primeira tarefa neste guia de início rápido mostra como criar um serviço de dados para expor um [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] do feed de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="f7ed5-105">The first task in this quickstart shows how to create a data service to expose an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed from the Northwind sample database.</span></span> <span data-ttu-id="f7ed5-106">Tópicos posteriores, você acessará o [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed usando um navegador da Web e também cria um [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] aplicativo cliente que consome o [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed usando bibliotecas de cliente.</span><span class="sxs-lookup"><span data-stu-id="f7ed5-106">In later topics, you will access the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed by using a Web browser, and also create a [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] client application that consumes the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed by using client libraries.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f7ed5-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="f7ed5-107">Prerequisites</span></span>  
 <span data-ttu-id="f7ed5-108">Para concluir este guia de início rápido, instale os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="f7ed5-108">To complete this quickstart, you must install the following components:</span></span>  
  
-   [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]<span data-ttu-id="f7ed5-109">.</span><span class="sxs-lookup"><span data-stu-id="f7ed5-109">.</span></span>  
  
-   <span data-ttu-id="f7ed5-110">Uma instância de [!INCLUDE[msCoName](../../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f7ed5-110">An instance of [!INCLUDE[msCoName](../../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f7ed5-111">Isso inclui o SQL Server Express, que é incluído em uma instalação padrão do [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f7ed5-111">This includes SQL Server Express, which is included in a default installation of [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span>  
  
-   <span data-ttu-id="f7ed5-112">O banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="f7ed5-112">The Northwind sample database.</span></span> <span data-ttu-id="f7ed5-113">Para baixar esse banco de dados de exemplo, consulte a página de download [bancos de dados do SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).</span><span class="sxs-lookup"><span data-stu-id="f7ed5-113">To download this sample database, see the download page, [Sample Databases for SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).</span></span>  
  
## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="f7ed5-114">Tarefas do guia de início rápido do WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="f7ed5-114">WCF Data Services Quickstart Tasks</span></span>  
 <span data-ttu-id="f7ed5-115">[Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md) (Criando o serviço de dados)</span><span class="sxs-lookup"><span data-stu-id="f7ed5-115">[Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md)</span></span>  
 <span data-ttu-id="f7ed5-116">Defina o aplicativo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], defina o modelo de dados, crie o serviço de dados e habilite o acesso aos recursos.</span><span class="sxs-lookup"><span data-stu-id="f7ed5-116">Define the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application, define the data model, create the data service, and enable access to resources.</span></span>  
  
 [<span data-ttu-id="f7ed5-117">Acessando o serviço de um navegador da Web</span><span class="sxs-lookup"><span data-stu-id="f7ed5-117">Accessing the Service from a Web Browser</span></span>](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)  
 <span data-ttu-id="f7ed5-118">Inicie o serviço no [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] e acesse o serviço enviando solicitações HTTP GET por meio de um navegador da Web ao feed exposto.</span><span class="sxs-lookup"><span data-stu-id="f7ed5-118">Start the service from [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>  
  
 [<span data-ttu-id="f7ed5-119">Criando o aplicativo cliente do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f7ed5-119">Creating the .NET Framework Client Application</span></span>](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)  
 <span data-ttu-id="f7ed5-120">Criar um [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] aplicativo cliente para consumir o [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed, associar dados a controles de Windows, alterar dados em controles associados e, em seguida, enviar as alterações de volta para o serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="f7ed5-120">Create a [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] client application to consume the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7ed5-121">Arquivos de projeto de uma versão completa do início rápido podem ser baixados do [exemplos de documentação do WCF Data Services](http://go.microsoft.com/fwlink/?LinkId=179994) página.</span><span class="sxs-lookup"><span data-stu-id="f7ed5-121">Project files from a completed version of the quickstart can be downloaded from the [WCF Data Services Documentation Samples](http://go.microsoft.com/fwlink/?LinkId=179994) page.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f7ed5-122">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="f7ed5-122">Next Steps</span></span>  
 <span data-ttu-id="f7ed5-123">[Iniciar o Quickstart](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="f7ed5-123">[Start the Quickstart](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7ed5-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7ed5-124">See Also</span></span>  
 [<span data-ttu-id="f7ed5-125">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="f7ed5-125">ADO.NET Entity Framework</span></span>](../../../../docs/framework/data/adonet/ef/index.md)
