---
title: Modelando e mapeando
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a219e4e3a58e3bd3e71bab3d3c41c87c393b20da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="modeling-and-mapping"></a><span data-ttu-id="c7fa3-102">Modelando e mapeando</span><span class="sxs-lookup"><span data-stu-id="c7fa3-102">Modeling and Mapping</span></span>
<span data-ttu-id="c7fa3-103">No [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], você pode definir o modelo conceitual, o modelo de armazenamento e o mapeamento entre os dois da maneira mais adequada ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c7fa3-103">In the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], you can define the conceptual model, storage model, and the mapping between the two in the way that best suits your application.</span></span> <span data-ttu-id="c7fa3-104">As ferramentas de modelo de dados de entidade no [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] permitem que você crie um.[ arquivo EDMX](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4) de um banco de dados ou um modelo de gráfico e atualize esse arquivo quando o banco de dados ou o modelo é alterado.</span><span class="sxs-lookup"><span data-stu-id="c7fa3-104">The Entity Data Model Tools in [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] allow you to create an .[edmx file](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4) from a database or a graphical model and then update that file when either the database or model changes.</span></span>  
  
 <span data-ttu-id="c7fa3-105">A partir do Entity Framework 4.1, você também pode criar um modelo programaticamente usando o desenvolvimento Code First.</span><span class="sxs-lookup"><span data-stu-id="c7fa3-105">Starting with the Entity Framework 4.1 you can also create a model programmatically using Code First development.</span></span> <span data-ttu-id="c7fa3-106">Há dois cenários diferentes para desenvolvimento Code First.</span><span class="sxs-lookup"><span data-stu-id="c7fa3-106">There are two different scenarios for Code First development.</span></span> <span data-ttu-id="c7fa3-107">Em ambos os casos, o desenvolvedor define um modelo codificando definições de classe do .NET Framework e, em seguida, opcionalmente especifica o mapeamento adicional ou a configuração usando Anotações de Dados ou a API fluente.</span><span class="sxs-lookup"><span data-stu-id="c7fa3-107">In both cases, the developer defines a model by coding .NET Framework class definitions, and then optionally specifies additional mapping or configuration by using Data Annotations or the fluent API.</span></span>  
  
 <span data-ttu-id="c7fa3-108">Para obter mais informações, consulte [criando e mapeando um modelo conceitual](http://go.microsoft.com/fwlink/?LinkId=235016).</span><span class="sxs-lookup"><span data-stu-id="c7fa3-108">For more information, see [Creating and Mapping a Conceptual Model](http://go.microsoft.com/fwlink/?LinkId=235016).</span></span>  
  
 <span data-ttu-id="c7fa3-109">Você também pode usar o gerador de EDM que acompanha o [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c7fa3-109">You can also use the EDM Generator, which is included with the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="c7fa3-110">O EdmGen.exe gera os arquivos .csdl, .ssdl e .msl de uma fonte de dados existente.</span><span class="sxs-lookup"><span data-stu-id="c7fa3-110">The EdmGen.exe generates the .csdl, .ssdl, and .msl files from an existing data source.</span></span> <span data-ttu-id="c7fa3-111">Você também pode criar manualmente o modelo e o conteúdo do mapeamento.</span><span class="sxs-lookup"><span data-stu-id="c7fa3-111">You can also manually create the model and mapping content.</span></span> <span data-ttu-id="c7fa3-112">Para obter mais informações, consulte [gerador de EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).</span><span class="sxs-lookup"><span data-stu-id="c7fa3-112">For more information, see [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).</span></span>
