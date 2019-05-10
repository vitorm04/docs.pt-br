---
title: Responsabilidades do desenvolvedor em substituir o comportamento padrão
ms.date: 03/30/2017
ms.assetid: c6909ddd-e053-46a8-980c-0e12a9797be1
ms.openlocfilehash: 4d895600eeaba9c410e9af359208361e83c42c4d
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64910594"
---
# <a name="responsibilities-of-the-developer-in-overriding-default-behavior"></a>Responsabilidades do desenvolvedor em substituir o comportamento padrão
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não impõe os seguintes requisitos, mas o comportamento será indefinido se esses requisitos não forem atendidos.  
  
- Substituindo o método não deve chamar <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ou <xref:System.Data.Linq.Table%601.Attach%2A>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] gera uma exceção se esses métodos são chamados em um método de substituição.  
  
- Substituir métodos não pode ser usado para começar, confirmar, ou parar uma transação. A operação de <xref:System.Data.Linq.DataContext.SubmitChanges%2A> é executada em uma transação. Uma transação aninhada interna pode interferir com a transação externo. Os métodos de substituição de carregamento podem iniciar uma transação somente após determinar que a operação não estiver sendo executada em <xref:System.Transactions.Transaction>.  
  
- Os métodos de substituição deverão seguir o mapeamento aplicável de concorrência otimista. O método de substituição é esperado lançar <xref:System.Data.Linq.ChangeConflictException> quando um conflito de simultaneidade otimista ocorre. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] captura essa exceção para que você possa processar corretamente a <xref:System.Data.Linq.DataContext.SubmitChanges%2A> opção fornecida na <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.  
  
- Crie (`Insert`) e métodos de substituição de `Update` são esperados fluir a voltar os valores para colunas base de dados - gerados correspondentes aos membros do objeto quando a operação é concluída com êxito.  
  
     Por exemplo, se `Order.OrderID` é mapeado para uma coluna de identidade (*autoincrement* chave primária), em seguida, o `InsertOrder()` método de substituição deve recuperar a ID de banco de dados gerado e definir o `Order.OrderID` membro para essa ID. Também, os membros de carimbo de data/hora devem ser atualizados para valores base de dados - gerados de carimbo de data/hora para certificar-se que os objetos atualizados são consistentes. A falha propagar os valores base de dados - gerados pode causar uma inconsistência entre o base de dados e objetos controlados por <xref:System.Data.Linq.DataContext>.  
  
- É responsabilidade do usuário chamar a API dinâmico correto. Por exemplo, o método de substituição de atualização, somente <xref:System.Data.Linq.DataContext.ExecuteDynamicUpdate%2A> pode ser chamado. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não detecta ou não verifica se o método dinâmico chamado corresponde a operação aplicável. Se um método inaplicável é chamado (por exemplo, <xref:System.Data.Linq.DataContext.ExecuteDynamicDelete%2A> para um objeto é atualizado), os resultados são indefinidos.  
  
- Finalmente, o método substituindo é esperado executar a operação indicada. A semântica [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] operações, como o carregamento adiantado, adiado carregando, e <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) requerem as substituições fornecer o serviço indicado. Por exemplo, uma carga substituir que apenas retorna uma coleção vazia sem verificar o conteúdo no banco de dados provavelmente resultará em dados inconsistentes.  
  
## <a name="see-also"></a>Consulte também

- [Personalizando as operações de inserção, atualização e exclusão](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
