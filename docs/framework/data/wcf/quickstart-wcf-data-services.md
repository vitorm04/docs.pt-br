---
title: Guia de Início Rápido (WCF Data Services)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: df6806cd77e7ff109d79f7ba61866763de4c7fc1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790365"
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="d2171-102">Guia de Início Rápido (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="d2171-102">Quickstart (WCF Data Services)</span></span>

<span data-ttu-id="d2171-103">Este [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] guia de início rápido ajuda você a se familiarizar com WCF Data Services e com uma série de tarefas que dão suporte aos tópicos em [introdução](getting-started-with-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d2171-103">This quickstart helps you become familiar with WCF Data Services and the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] through a series of tasks that support the topics in [Getting Started](getting-started-with-wcf-data-services.md).</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="d2171-104">O que você aprenderá</span><span class="sxs-lookup"><span data-stu-id="d2171-104">What you'll learn</span></span>

<span data-ttu-id="d2171-105">A primeira tarefa neste guia de início rápido mostra como criar um serviço de dados para expor um feed OData do banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="d2171-105">The first task in this quickstart shows how to create a data service to expose an OData feed from the Northwind sample database.</span></span> <span data-ttu-id="d2171-106">Nos tópicos posteriores, você acessará o feed OData usando um navegador da Web e também criará um aplicativo cliente Windows Presentation Foundation (WPF) que consome o feed OData usando bibliotecas de cliente.</span><span class="sxs-lookup"><span data-stu-id="d2171-106">In later topics, you will access the OData feed by using a Web browser, and also create a Windows Presentation Foundation (WPF) client application that consumes the OData feed by using client libraries.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d2171-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="d2171-107">Prerequisites</span></span>

<span data-ttu-id="d2171-108">Para concluir este guia de início rápido, instale os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="d2171-108">To complete this quickstart, you must install the following components:</span></span>

- <span data-ttu-id="d2171-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d2171-109">Visual Studio</span></span>

- <span data-ttu-id="d2171-110">Uma instância de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d2171-110">An instance of SQL Server.</span></span> <span data-ttu-id="d2171-111">Isso inclui SQL Server Express, que está incluído em uma instalação padrão do Visual Studio 2015 ou como parte da carga de trabalho de **armazenamento e processamento de dados** no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="d2171-111">This includes SQL Server Express, which is included in a default installation of Visual Studio 2015, or as part of the **Data storage and processing** workload in Visual Studio 2017.</span></span>

- <span data-ttu-id="d2171-112">O banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="d2171-112">The Northwind sample database.</span></span> <span data-ttu-id="d2171-113">Para baixar esse banco de dados de exemplo, consulte a página de download, [bancos de dados de exemplo para SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span><span class="sxs-lookup"><span data-stu-id="d2171-113">To download this sample database, see the download page, [Sample Databases for SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span></span>

## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="d2171-114">Tarefas de início rápido do WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="d2171-114">WCF data services quickstart tasks</span></span>

 [<span data-ttu-id="d2171-115">Criar o serviço de dados</span><span class="sxs-lookup"><span data-stu-id="d2171-115">Create the Data Service</span></span>](creating-the-data-service.md)

 <span data-ttu-id="d2171-116">Defina o aplicativo ASP.NET, defina o modelo de dados, crie o serviço de dados e habilite o acesso aos recursos.</span><span class="sxs-lookup"><span data-stu-id="d2171-116">Define the ASP.NET application, define the data model, create the data service, and enable access to resources.</span></span>

 [<span data-ttu-id="d2171-117">Acessar o serviço de um navegador da Web</span><span class="sxs-lookup"><span data-stu-id="d2171-117">Access the Service from a Web Browser</span></span>](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 <span data-ttu-id="d2171-118">Inicie o serviço do Visual Studio e acesse o serviço enviando solicitações HTTP GET por meio de um navegador da Web para o feed exposto.</span><span class="sxs-lookup"><span data-stu-id="d2171-118">Start the service from Visual Studio and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>

 [<span data-ttu-id="d2171-119">Criar o aplicativo cliente .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d2171-119">Create the .NET Framework Client Application</span></span>](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 <span data-ttu-id="d2171-120">Crie um aplicativo WPF para consumir o feed OData, associar dados a controles do Windows, alterar dados nos controles vinculados e enviar as alterações de volta para o serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="d2171-120">Create a WPF app to consume the OData feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>

> [!NOTE]
> <span data-ttu-id="d2171-121">Os arquivos de projeto de uma versão concluída do guia de início rápido podem ser baixados na página de [exemplos da documentação WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=179994) .</span><span class="sxs-lookup"><span data-stu-id="d2171-121">Project files from a completed version of the quickstart can be downloaded from the [WCF Data Services Documentation Samples](https://go.microsoft.com/fwlink/?LinkId=179994) page.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d2171-122">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="d2171-122">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d2171-123">Iniciar o início rápido</span><span class="sxs-lookup"><span data-stu-id="d2171-123">Start the quickstart</span></span>](creating-the-data-service.md)

## <a name="see-also"></a><span data-ttu-id="d2171-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2171-124">See also</span></span>

- [<span data-ttu-id="d2171-125">Entity Framework do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d2171-125">ADO.NET Entity Framework</span></span>](../adonet/ef/index.md)
