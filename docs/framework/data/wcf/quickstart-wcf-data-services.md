---
title: Guia de Início Rápido (WCF Data Services)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: f945d33a4fc789b3c73c1c80040fc8527301758b
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121221"
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="4c306-102">Guia de Início Rápido (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="4c306-102">Quickstart (WCF Data Services)</span></span>

<span data-ttu-id="4c306-103">Esse rápido início ajuda você a se familiarizar com os Serviços de Dados WCF e o Protocolo de Dados Abertos (OData) através de uma série de tarefas que suportam os tópicos em [Getting Started](getting-started-with-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="4c306-103">This quickstart helps you become familiar with WCF Data Services and the Open Data Protocol (OData) through a series of tasks that support the topics in [Getting Started](getting-started-with-wcf-data-services.md).</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="4c306-104">O que você aprenderá</span><span class="sxs-lookup"><span data-stu-id="4c306-104">What you'll learn</span></span>

<span data-ttu-id="4c306-105">A primeira tarefa neste quickstart mostra como criar um serviço de dados para expor um feed OData do banco de dados de amostras do Northwind.</span><span class="sxs-lookup"><span data-stu-id="4c306-105">The first task in this quickstart shows how to create a data service to expose an OData feed from the Northwind sample database.</span></span> <span data-ttu-id="4c306-106">Em tópicos posteriores, você acessará o feed OData usando um navegador da Web e também criará um aplicativo cliente da Windows Presentation Foundation (WPF) que consome o feed OData usando bibliotecas de clientes.</span><span class="sxs-lookup"><span data-stu-id="4c306-106">In later topics, you will access the OData feed by using a Web browser, and also create a Windows Presentation Foundation (WPF) client application that consumes the OData feed by using client libraries.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4c306-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="4c306-107">Prerequisites</span></span>

<span data-ttu-id="4c306-108">Para concluir esse quickstart, instale os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="4c306-108">To complete this quickstart, install the following components:</span></span>

- <span data-ttu-id="4c306-109">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4c306-109">Visual Studio</span></span>

- <span data-ttu-id="4c306-110">Um exemplo de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4c306-110">An instance of SQL Server.</span></span> <span data-ttu-id="4c306-111">Isso inclui o SQL Server Express, que está incluído em uma instalação padrão do Visual Studio 2015, ou como parte da carga de trabalho de **armazenamento e processamento** de dados no Visual Studio 2017 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="4c306-111">This includes SQL Server Express, which is included in a default installation of Visual Studio 2015, or as part of the **Data storage and processing** workload in Visual Studio 2017 or later.</span></span>

- <span data-ttu-id="4c306-112">O banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="4c306-112">The Northwind sample database.</span></span> <span data-ttu-id="4c306-113">Para instalar o banco de dados, execute o script Transact-SQL dos bancos de dados de [amostra de Northwind e pubs para o Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span><span class="sxs-lookup"><span data-stu-id="4c306-113">To install the database, run the Transact-SQL script from [Northwind and pubs sample databases for Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span></span>

## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="4c306-114">Serviços de dados WCF iniciam tarefas de início rápido</span><span class="sxs-lookup"><span data-stu-id="4c306-114">WCF data services quickstart tasks</span></span>

 [<span data-ttu-id="4c306-115">Crie o Serviço de Dados</span><span class="sxs-lookup"><span data-stu-id="4c306-115">Create the Data Service</span></span>](creating-the-data-service.md)

 <span data-ttu-id="4c306-116">Defina o aplicativo ASP.NET, defina o modelo de dados, crie o serviço de dados e habilite o acesso aos recursos.</span><span class="sxs-lookup"><span data-stu-id="4c306-116">Define the ASP.NET application, define the data model, create the data service, and enable access to resources.</span></span>

 [<span data-ttu-id="4c306-117">Acesse o Serviço a partir de um navegador da Web</span><span class="sxs-lookup"><span data-stu-id="4c306-117">Access the Service from a Web Browser</span></span>](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 <span data-ttu-id="4c306-118">Inicie o serviço no Visual Studio e acesse o serviço enviando solicitações HTTP GET através de um navegador da Web para o feed exposto.</span><span class="sxs-lookup"><span data-stu-id="4c306-118">Start the service from Visual Studio and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>

 [<span data-ttu-id="4c306-119">Criar o aplicativo cliente framework .NET</span><span class="sxs-lookup"><span data-stu-id="4c306-119">Create the .NET Framework Client Application</span></span>](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 <span data-ttu-id="4c306-120">Crie um aplicativo WPF para consumir o feed OData, vincule dados aos controles do Windows, altere dados nos controles vinculados e envie as alterações de volta para o serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="4c306-120">Create a WPF app to consume the OData feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>

> [!NOTE]
> <span data-ttu-id="4c306-121">Os arquivos do projeto de uma versão completa do quickstart podem ser baixados do [GitHub](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client)).</span><span class="sxs-lookup"><span data-stu-id="4c306-121">Project files from a completed version of the quickstart can be downloaded from [GitHub](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client)).</span></span>

## <a name="next-steps"></a><span data-ttu-id="4c306-122">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="4c306-122">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4c306-123">Comece o quickstart</span><span class="sxs-lookup"><span data-stu-id="4c306-123">Start the quickstart</span></span>](creating-the-data-service.md)

## <a name="see-also"></a><span data-ttu-id="4c306-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="4c306-124">See also</span></span>

- [<span data-ttu-id="4c306-125">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="4c306-125">ADO.NET Entity Framework</span></span>](../adonet/ef/index.md)
