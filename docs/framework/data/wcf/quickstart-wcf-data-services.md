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
# <a name="quickstart-wcf-data-services"></a>Guia de Início Rápido (WCF Data Services)

Esse rápido início ajuda você a se familiarizar com os Serviços de Dados WCF e o Protocolo de Dados Abertos (OData) através de uma série de tarefas que suportam os tópicos em [Getting Started](getting-started-with-wcf-data-services.md).

## <a name="what-youll-learn"></a>O que você aprenderá

A primeira tarefa neste quickstart mostra como criar um serviço de dados para expor um feed OData do banco de dados de amostras do Northwind. Em tópicos posteriores, você acessará o feed OData usando um navegador da Web e também criará um aplicativo cliente da Windows Presentation Foundation (WPF) que consome o feed OData usando bibliotecas de clientes.

## <a name="prerequisites"></a>Pré-requisitos

Para concluir esse quickstart, instale os seguintes componentes:

- Visual Studio

- Um exemplo de SQL Server. Isso inclui o SQL Server Express, que está incluído em uma instalação padrão do Visual Studio 2015, ou como parte da carga de trabalho de **armazenamento e processamento** de dados no Visual Studio 2017 ou posterior.

- O banco de dados de exemplo Northwind. Para instalar o banco de dados, execute o script Transact-SQL dos bancos de dados de [amostra de Northwind e pubs para o Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).

## <a name="wcf-data-services-quickstart-tasks"></a>Serviços de dados WCF iniciam tarefas de início rápido

 [Crie o Serviço de Dados](creating-the-data-service.md)

 Defina o aplicativo ASP.NET, defina o modelo de dados, crie o serviço de dados e habilite o acesso aos recursos.

 [Acesse o Serviço a partir de um navegador da Web](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 Inicie o serviço no Visual Studio e acesse o serviço enviando solicitações HTTP GET através de um navegador da Web para o feed exposto.

 [Criar o aplicativo cliente framework .NET](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 Crie um aplicativo WPF para consumir o feed OData, vincule dados aos controles do Windows, altere dados nos controles vinculados e envie as alterações de volta para o serviço de dados.

> [!NOTE]
> Os arquivos do projeto de uma versão completa do quickstart podem ser baixados do [GitHub](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client)).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Comece o quickstart](creating-the-data-service.md)

## <a name="see-also"></a>Confira também

- [ADO.NET Entity Framework](../adonet/ef/index.md)
