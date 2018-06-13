---
title: 'Personalizando operações: Visão geral'
ms.date: 03/30/2017
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
ms.openlocfilehash: d495632faf2f57df21d07e0be85244d7ba9d9da7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359591"
---
# <a name="customizing-operations-overview"></a>Personalizando operações: Visão geral
Por padrão, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] gera SQL dinâmico para inserção, atualização e operações de exclusão com base no mapeamento. No entanto, na prática, você geralmente deseja adicionar sua própria lógica de negócios para fornecer segurança, validação e assim por diante.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] técnicas para personalizar essas operações incluem o seguinte.  
  
## <a name="loading-options"></a>Opções de carregamento  
 Nas consultas, você pode controlar como os dados relacionados ao seu destino principal são recuperados quando você se conecta ao base de dados. Essa funcionalidade é implementada amplamente usando <xref:System.Data.Linq.DataLoadOptions>. Para obter mais informações, consulte [adiado contra Carregando imediata](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
## <a name="partial-methods"></a>Métodos parciais  
 No mapeamento padrão, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fornece métodos parciais para ajudá-lo a implementar a lógica corporativa. Para obter mais informações, consulte [adicionando negócios lógica por usando métodos parciais](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md).  
  
## <a name="stored-procedures-and-user-defined-functions"></a>Procedimentos e funções definidas pelo usuário armazenados  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] oferece suporte ao uso de procedimentos armazenados e funções definidas pelo usuário. Os procedimentos armazenados são usados para personalizar operações. Para obter mais informações, consulte [Procedimentos armazenados](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).  
  
## <a name="see-also"></a>Consulte também  
 [Personalizando as operações de inserção, atualização e exclusão](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
