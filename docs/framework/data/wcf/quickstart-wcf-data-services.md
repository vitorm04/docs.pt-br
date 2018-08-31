---
title: Guia de Início Rápido (WCF Data Services)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: f20ffcf356aa0493b1e2356746d9ad7b27d9a1aa
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43330861"
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="7fa6a-102">Guia de Início Rápido (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="7fa6a-102">Quickstart (WCF Data Services)</span></span>

<span data-ttu-id="7fa6a-103">Neste início rápido ajuda você a se familiarizar com o WCF Data Services e o [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] por meio de uma série de tarefas que dão suporte os tópicos [Introdução](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="7fa6a-103">This quickstart helps you become familiar with WCF Data Services and the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] through a series of tasks that support the topics in [Getting Started](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md).</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="7fa6a-104">O que você aprenderá</span><span class="sxs-lookup"><span data-stu-id="7fa6a-104">What you'll learn</span></span>

<span data-ttu-id="7fa6a-105">A primeira tarefa neste início rápido mostra como criar um serviço de dados para expor um feed OData em um banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="7fa6a-105">The first task in this quickstart shows how to create a data service to expose an OData feed from the Northwind sample database.</span></span> <span data-ttu-id="7fa6a-106">Em tópicos posteriores, você acessará o OData feed usando um navegador da Web e também criar um Windows Presentation Foundation (WPF) aplicativo cliente que consome o OData feed usando bibliotecas de cliente.</span><span class="sxs-lookup"><span data-stu-id="7fa6a-106">In later topics, you will access the OData feed by using a Web browser, and also create a Windows Presentation Foundation (WPF) client application that consumes the OData feed by using client libraries.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7fa6a-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7fa6a-107">Prerequisites</span></span>

<span data-ttu-id="7fa6a-108">Para concluir este guia de início rápido, instale os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="7fa6a-108">To complete this quickstart, you must install the following components:</span></span>

- <span data-ttu-id="7fa6a-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7fa6a-109">Visual Studio</span></span>

- <span data-ttu-id="7fa6a-110">Uma instância do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7fa6a-110">An instance of SQL Server.</span></span> <span data-ttu-id="7fa6a-111">Isso inclui o SQL Server Express, que é incluído em uma instalação padrão do Visual Studio 2015 ou como parte do **armazenamento de dados e processamento** carga de trabalho no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="7fa6a-111">This includes SQL Server Express, which is included in a default installation of Visual Studio 2015, or as part of the **Data storage and processing** workload in Visual Studio 2017.</span></span>

- <span data-ttu-id="7fa6a-112">O banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="7fa6a-112">The Northwind sample database.</span></span> <span data-ttu-id="7fa6a-113">Para baixar esse banco de dados de exemplo, consulte a página de download [bancos de dados do SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span><span class="sxs-lookup"><span data-stu-id="7fa6a-113">To download this sample database, see the download page, [Sample Databases for SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span></span>

## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="7fa6a-114">Tarefas de início rápido do WCF data services</span><span class="sxs-lookup"><span data-stu-id="7fa6a-114">WCF data services quickstart tasks</span></span>

 [<span data-ttu-id="7fa6a-115">Criar o serviço de dados</span><span class="sxs-lookup"><span data-stu-id="7fa6a-115">Create the Data Service</span></span>](../../../../docs/framework/data/wcf/creating-the-data-service.md)

 <span data-ttu-id="7fa6a-116">Defina o aplicativo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], defina o modelo de dados, crie o serviço de dados e habilite o acesso aos recursos.</span><span class="sxs-lookup"><span data-stu-id="7fa6a-116">Define the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application, define the data model, create the data service, and enable access to resources.</span></span>

 [<span data-ttu-id="7fa6a-117">Acessar o serviço de um navegador da Web</span><span class="sxs-lookup"><span data-stu-id="7fa6a-117">Access the Service from a Web Browser</span></span>](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 <span data-ttu-id="7fa6a-118">Inicie o serviço do Visual Studio e acesse o serviço enviando solicitações HTTP GET por meio de um navegador da Web ao feed exposto.</span><span class="sxs-lookup"><span data-stu-id="7fa6a-118">Start the service from Visual Studio and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>

 [<span data-ttu-id="7fa6a-119">Criar o aplicativo cliente do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7fa6a-119">Create the .NET Framework Client Application</span></span>](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 <span data-ttu-id="7fa6a-120">Criar um aplicativo do WPF para consumir o feed OData, associar dados aos controles do Windows, altere os dados em controles associados e, em seguida, enviar que as alterações de volta para o serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="7fa6a-120">Create a WPF app to consume the OData feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>

> [!NOTE]
> <span data-ttu-id="7fa6a-121">Arquivos de projeto de uma versão completa do início rápido podem ser baixados do [exemplos de documentação do WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=179994) página.</span><span class="sxs-lookup"><span data-stu-id="7fa6a-121">Project files from a completed version of the quickstart can be downloaded from the [WCF Data Services Documentation Samples](https://go.microsoft.com/fwlink/?LinkId=179994) page.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7fa6a-122">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="7fa6a-122">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7fa6a-123">Iniciar o guia de início rápido</span><span class="sxs-lookup"><span data-stu-id="7fa6a-123">Start the quickstart</span></span>](../../../../docs/framework/data/wcf/creating-the-data-service.md)

## <a name="see-also"></a><span data-ttu-id="7fa6a-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7fa6a-124">See also</span></span>

- [<span data-ttu-id="7fa6a-125">Entity Framework do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7fa6a-125">ADO.NET Entity Framework</span></span>](../../../../docs/framework/data/adonet/ef/index.md)
