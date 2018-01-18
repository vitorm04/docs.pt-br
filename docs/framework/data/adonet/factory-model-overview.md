---
title: "Visão geral do modelo de fábrica"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5dc81c4-7554-44b9-b513-769bd61e2e7b
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0194cd6789ae6ddebeeee65abf1a4fca4a2bc0d6
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="factory-model-overview"></a><span data-ttu-id="358d2-102">Visão geral do modelo de fábrica</span><span class="sxs-lookup"><span data-stu-id="358d2-102">Factory Model Overview</span></span>
<span data-ttu-id="358d2-103">O ADO.NET 2.0 introduziu novas classes base no <xref:System.Data.Common> namespace.</span><span class="sxs-lookup"><span data-stu-id="358d2-103">ADO.NET 2.0 introduced new base classes in the <xref:System.Data.Common> namespace.</span></span> <span data-ttu-id="358d2-104">As classes base serão abstratas, o que significa que eles não podem ser instanciados diretamente.</span><span class="sxs-lookup"><span data-stu-id="358d2-104">The base classes are abstract, which means that they can't be directly instantiated.</span></span> <span data-ttu-id="358d2-105">Eles incluem <xref:System.Data.Common.DbConnection>, <xref:System.Data.Common.DbCommand>, e <xref:System.Data.Common.DbDataAdapter> e são compartilhados pelos provedores de dados do .NET Framework, como <xref:System.Data.SqlClient> e <xref:System.Data.OleDb>.</span><span class="sxs-lookup"><span data-stu-id="358d2-105">They include <xref:System.Data.Common.DbConnection>, <xref:System.Data.Common.DbCommand>, and <xref:System.Data.Common.DbDataAdapter> and are shared by the .NET Framework data providers, such as <xref:System.Data.SqlClient> and <xref:System.Data.OleDb>.</span></span> <span data-ttu-id="358d2-106">A adição de classes base simplifica adicionando funcionalidade para os provedores de dados do .NET Framework sem a necessidade de criar novas interfaces.</span><span class="sxs-lookup"><span data-stu-id="358d2-106">The addition of base classes simplifies adding functionality to the .NET Framework data providers without having to create new interfaces.</span></span>  
  
 <span data-ttu-id="358d2-107">O ADO.NET 2.0 também introduziu classes base abstratas, que permitem que um desenvolvedor gravar o código de acesso a dados genéricos que não dependem de um provedor de dados específico.</span><span class="sxs-lookup"><span data-stu-id="358d2-107">ADO.NET 2.0 also introduced abstract base classes, which enable a developer to write generic data access code that does not depend on a specific data provider.</span></span>  
  
## <a name="the-factory-design-pattern"></a><span data-ttu-id="358d2-108">O padrão de Design de fábrica</span><span class="sxs-lookup"><span data-stu-id="358d2-108">The Factory Design Pattern</span></span>  
 <span data-ttu-id="358d2-109">O modelo de programação para escrever código independente de provedor baseia-se no uso do padrão de design "fábrica", que usa uma única API para acessar bancos de dados em vários provedores.</span><span class="sxs-lookup"><span data-stu-id="358d2-109">The programming model for writing provider-independent code is based on the use of the "factory" design pattern, which uses a single API to access databases across multiple providers.</span></span> <span data-ttu-id="358d2-110">Esse padrão é denominado adequadamente, pois ele exige o uso de um objeto especializado exclusivamente para criar outros objetos, como uma fábrica do mundo real.</span><span class="sxs-lookup"><span data-stu-id="358d2-110">This pattern is aptly named, as it calls for the use of a specialized object solely to create other objects, much like a real-world factory.</span></span> <span data-ttu-id="358d2-111">Para obter uma descrição mais detalhada do padrão de design de fábrica, consulte "[escrever o código de acesso de dados genérico no ASP.NET 2.0 e o ADO.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=55915)" e "Genérico de codificação com o ADO.NET 2.0 Base de Classes e fábricas de" [http:// MSDN.microsoft.com/library/default.asp?URL=/Library/dnvs05/HTML/vsgenerics.asp](http://msdn.microsoft.com/library/default.asp?url=/library/dnvs05/html/vsgenerics.asp) no MSDN.</span><span class="sxs-lookup"><span data-stu-id="358d2-111">For a more detailed description of the factory design pattern, see "[Writing Generic Data Access Code in ASP.NET 2.0 and ADO.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=55915)" and "Generic Coding with the ADO.NET 2.0 Base Classes and Factories" [http://msdn.microsoft.com/library/default.asp?url=/library/dnvs05/html/vsgenerics.asp](http://msdn.microsoft.com/library/default.asp?url=/library/dnvs05/html/vsgenerics.asp) on MSDN.</span></span>  
  
 <span data-ttu-id="358d2-112">Começando com o ADO.NET 2.0, o <xref:System.Data.Common.DbProviderFactories> classe fornece `static` (ou `Shared` no Visual Basic) métodos para criar um <xref:System.Data.Common.DbProviderFactory> instância.</span><span class="sxs-lookup"><span data-stu-id="358d2-112">Starting with ADO.NET 2.0, the <xref:System.Data.Common.DbProviderFactories> class provides `static` (or `Shared` in Visual Basic) methods for creating a <xref:System.Data.Common.DbProviderFactory> instance.</span></span> <span data-ttu-id="358d2-113">A instância, em seguida, retorna um objeto fortemente tipado correto com base em informações do provedor e a cadeia de caracteres de conexão fornecido no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="358d2-113">The instance then returns a correct strongly typed object based on provider information and the connection string supplied at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="358d2-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="358d2-114">See Also</span></span>  
 [<span data-ttu-id="358d2-115">Obtendo um DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="358d2-115">Obtaining a DbProviderFactory</span></span>](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 [<span data-ttu-id="358d2-116">DbConnection, DbCommand e DbException</span><span class="sxs-lookup"><span data-stu-id="358d2-116">DbConnection, DbCommand and DbException</span></span>](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [<span data-ttu-id="358d2-117">Modificando dados com um DbDataAdapter</span><span class="sxs-lookup"><span data-stu-id="358d2-117">Modifying Data with a DbDataAdapter</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 <span data-ttu-id="358d2-118">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="358d2-118">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
