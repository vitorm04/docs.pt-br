---
title: Responsabilidades do desenvolvedor em substituir o comportamento padrão
ms.date: 03/30/2017
ms.assetid: c6909ddd-e053-46a8-980c-0e12a9797be1
ms.openlocfilehash: 90b8eedcc80c330a39efe97b6427beebeca913f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="responsibilities-of-the-developer-in-overriding-default-behavior"></a>Responsabilidades do desenvolvedor em substituir o comportamento padrão
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não impõe os seguintes requisitos, mas o comportamento será indefinido se esses requisitos não forem atendidos.  
  
-   Substituindo o método não deve chamar <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ou <xref:System.Data.Linq.Table%601.Attach%2A>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] gera uma exceção se esses métodos são chamados em um método de substituição.  
  
-   Substituir métodos não pode ser usado para começar, confirmar, ou parar uma transação. A operação de <xref:System.Data.Linq.DataContext.SubmitChanges%2A> é executada em uma transação. Uma transação aninhada interna pode interferir com a transação externo. Os métodos de substituição de carregamento podem iniciar uma transação somente após determinar que a operação não estiver sendo executada em <xref:System.Transactions.Transaction>.  
  
-   Os métodos de substituição deverão seguir o mapeamento aplicável de concorrência otimista. O método de substituição é esperado lançar <xref:System.Data.Linq.ChangeConflictException> quando um conflito de simultaneidade otimista ocorre. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] captura essa exceção para que você possa processar corretamente a <xref:System.Data.Linq.DataContext.SubmitChanges%2A> opção fornecida no <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.  
  
-   Crie (`Insert`) e métodos de substituição de `Update` são esperados fluir a voltar os valores para colunas base de dados - gerados correspondentes aos membros do objeto quando a operação é concluída com êxito.  
  
     Por exemplo, se `Order.OrderID` é mapeado para uma coluna de identidade (*autoincrement* chave primária), em seguida, o `InsertOrder()` método de substituição deve recuperar a ID de banco de dados gerado e defina o `Order.OrderID` membro para essa ID. Também, os membros de carimbo de data/hora devem ser atualizados para valores base de dados - gerados de carimbo de data/hora para certificar-se que os objetos atualizados são consistentes. A falha propagar os valores base de dados - gerados pode causar uma inconsistência entre o base de dados e objetos controlados por <xref:System.Data.Linq.DataContext>.  
  
-   É responsabilidade do usuário chamar a API dinâmico correto. Por exemplo, o método de substituição de atualização, somente <xref:System.Data.Linq.DataContext.ExecuteDynamicUpdate%2A> pode ser chamado. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não detecta ou não verifica se o método dinâmico chamado corresponde a operação aplicável. Se um método inaplicável é chamado (por exemplo, <xref:System.Data.Linq.DataContext.ExecuteDynamicDelete%2A> para um objeto é atualizado), os resultados são indefinidos.  
  
-   Finalmente, o método substituindo é esperado executar a operação indicada. A semântica de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] operações como carregamento adiantado, adiada carregar, e <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) exigem as substituições para fornecer o serviço indicado. Por exemplo, uma carga de substituição que apenas retorna uma coleção vazia sem verificar o conteúdo do banco de dados provavelmente resultará em dados inconsistentes.  
  
## <a name="see-also"></a>Consulte também  
 [Personalizando as operações de inserção, atualização e exclusão](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
