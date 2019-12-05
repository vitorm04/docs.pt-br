---
title: Guia de Início Rápido (WCF Data Services)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: df3151dfd3628231d84d2d128c61d1c0b6b0d48e
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800357"
---
# <a name="quickstart-wcf-data-services"></a>Guia de Início Rápido (WCF Data Services)

Este guia de início rápido ajuda você a se familiarizar com WCF Data Services e o Protocolo Open Data (OData) por meio de uma série de tarefas que dão suporte aos tópicos em [introdução](getting-started-with-wcf-data-services.md).

## <a name="what-youll-learn"></a>O que você aprenderá

A primeira tarefa neste guia de início rápido mostra como criar um serviço de dados para expor um feed OData do banco de dados de exemplo Northwind. Nos tópicos posteriores, você acessará o feed OData usando um navegador da Web e também criará um aplicativo cliente Windows Presentation Foundation (WPF) que consome o feed OData usando bibliotecas de cliente.

## <a name="prerequisites"></a>{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}

Para concluir este guia de início rápido, instale os seguintes componentes:

- {1&gt;Visual Studio&lt;1}

- Uma instância de SQL Server. Isso inclui SQL Server Express, que está incluído em uma instalação padrão do Visual Studio 2015 ou como parte da carga de trabalho de **armazenamento e processamento de dados** no visual Studio 2017 ou posterior.

- O banco de dados de exemplo Northwind. Para baixar esse banco de dados de exemplo, consulte a página de download, [bancos de dados de exemplo para SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).

## <a name="wcf-data-services-quickstart-tasks"></a>Tarefas de início rápido do WCF Data Services

 [Criar o serviço de dados](creating-the-data-service.md)

 Defina o aplicativo ASP.NET, defina o modelo de dados, crie o serviço de dados e habilite o acesso aos recursos.

 [Acessar o serviço de um navegador da Web](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 Inicie o serviço do Visual Studio e acesse o serviço enviando solicitações HTTP GET por meio de um navegador da Web para o feed exposto.

 [Criar o aplicativo cliente .NET Framework](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 Crie um aplicativo WPF para consumir o feed OData, associar dados a controles do Windows, alterar dados nos controles vinculados e enviar as alterações de volta para o serviço de dados.

> [!NOTE]
> Os arquivos de projeto de uma versão concluída do guia de início rápido podem ser baixados na página de [exemplos da documentação WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=179994) .

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

> [!div class="nextstepaction"]
> [Iniciar o início rápido](creating-the-data-service.md)

## <a name="see-also"></a>Consulte também

- [Entity Framework do ADO.NET](../adonet/ef/index.md)
