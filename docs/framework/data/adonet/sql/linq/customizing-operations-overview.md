---
title: "Personalizando operações: Visão geral"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7653ca137c93da5174e0ddcd1ced8bdfceaa9edc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="customizing-operations-overview"></a>Personalizando operações: Visão geral
Por padrão, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] gera SQL dinâmico para inserção, atualização e operações de exclusão com base no mapeamento. No entanto, na prática, você geralmente deseja adicionar sua própria lógica de negócios para fornecer segurança, validação e assim por diante.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]técnicas para personalizar essas operações incluem o seguinte.  
  
## <a name="loading-options"></a>Opções de carregamento  
 Nas consultas, você pode controlar como os dados relacionados ao seu destino principal são recuperados quando você se conecta ao base de dados. Essa funcionalidade é implementada amplamente usando <xref:System.Data.Linq.DataLoadOptions>. Para obter mais informações, consulte [adiado contra Carregando imediata](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
## <a name="partial-methods"></a>Métodos parciais  
 No mapeamento padrão, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fornece métodos parciais para ajudá-lo a implementar a lógica corporativa. Para obter mais informações, consulte [adicionando negócios lógica por usando métodos parciais](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md).  
  
## <a name="stored-procedures-and-user-defined-functions"></a>Procedimentos e funções definidas pelo usuário armazenados  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]oferece suporte ao uso de procedimentos armazenados e funções definidas pelo usuário. Os procedimentos armazenados são usados para personalizar operações. Para obter mais informações, consulte [Procedimentos armazenados](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).  
  
## <a name="see-also"></a>Consulte também  
 [Personalizando a inserção, atualização e exclusão de operações](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
