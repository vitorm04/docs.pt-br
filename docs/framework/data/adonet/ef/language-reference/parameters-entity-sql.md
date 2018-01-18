---
title: "Parâmetros (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: bb631a752bfe0e741b654ec6774a14c82c89157c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="44c64-102">Parâmetros (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="44c64-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="44c64-103">Os parâmetros são variáveis que são definidos fora de [!INCLUDE[esql](../../../../../../includes/esql-md.md)], geralmente através de uma associação API que é usada por uma linguagem de host.</span><span class="sxs-lookup"><span data-stu-id="44c64-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="44c64-104">Cada parâmetro tem um nome e um tipo.</span><span class="sxs-lookup"><span data-stu-id="44c64-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="44c64-105">Nomes de parâmetro são definidos em expressões de consulta com o em (@) símbolo como um prefixo.</span><span class="sxs-lookup"><span data-stu-id="44c64-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="44c64-106">Isso remove a ambiguidade dos-los de nomes de propriedades ou outros nomes que são definidos na consulta.</span><span class="sxs-lookup"><span data-stu-id="44c64-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="44c64-107">O host linguagem que associa API fornece APIs para parâmetros de associação.</span><span class="sxs-lookup"><span data-stu-id="44c64-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44c64-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="44c64-108">Example</span></span>  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="44c64-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44c64-109">See Also</span></span>  
 [<span data-ttu-id="44c64-110">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="44c64-110">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="44c64-111">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="44c64-111">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
