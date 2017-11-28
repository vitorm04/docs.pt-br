---
title: . (Acesso de membro) (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6c9d5d8f2c90273b316379d3c2803835bab3faef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="-member-access-entity-sql"></a><span data-ttu-id="8acb4-103">.</span><span class="sxs-lookup"><span data-stu-id="8acb4-103">.</span></span> <span data-ttu-id="8acb4-104">(Acesso de membro) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8acb4-104">(Member Access) (Entity SQL)</span></span>
<span data-ttu-id="8acb4-105">O operador ponto (.) é o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operador de acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="8acb4-105">The dot operator (.) is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] member access operator.</span></span> <span data-ttu-id="8acb4-106">Você usa o operador de acesso de membro para produzir o valor de uma propriedade ou um campo de uma instância do tipo estrutural de modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="8acb4-106">You use the member access operator to yield the value of a property or field of an instance of structural conceptual model type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8acb4-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8acb4-107">Syntax</span></span>  
  
```  
expression.identifier  
```  
  
## <a name="arguments"></a><span data-ttu-id="8acb4-108">Arguments</span><span class="sxs-lookup"><span data-stu-id="8acb4-108">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="8acb4-109">Uma instância de um tipo estrutural de modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="8acb4-109">An instance of a structural conceptual model type.</span></span>  
  
 `identifier`  
 <span data-ttu-id="8acb4-110">Uma propriedade ou um campo que pertençam a uma instância do objeto.</span><span class="sxs-lookup"><span data-stu-id="8acb4-110">A property or field that belongs to an object instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8acb4-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="8acb4-111">Remarks</span></span>  
 <span data-ttu-id="8acb4-112">O operador ponto (.) pode ser usado para extrair campos de um registro, semelhante a extrair propriedades de um complexo ou tipo de objeto.</span><span class="sxs-lookup"><span data-stu-id="8acb4-112">The dot (.) operator may be used to extract fields from a record, similar to extracting properties of a complex or entity type.</span></span> <span data-ttu-id="8acb4-113">Por exemplo, se n do nome de tipo é um membro de tipo Person e p é uma instância de tipo Person, p.n é uma expressão de acesso de membro válido que gera um valor de tipo de nome.</span><span class="sxs-lookup"><span data-stu-id="8acb4-113">For example, if n of type Name is a member of type Person, and p is an instance of type Person, then p.n is a legal member access expression that yields a value of type Name.</span></span>  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a><span data-ttu-id="8acb4-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8acb4-114">See Also</span></span>  
 [<span data-ttu-id="8acb4-115">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8acb4-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
