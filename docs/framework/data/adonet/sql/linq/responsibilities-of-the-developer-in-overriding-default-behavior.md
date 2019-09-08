---
title: Responsabilidades do desenvolvedor em substituir o comportamento padrão
ms.date: 03/30/2017
ms.assetid: c6909ddd-e053-46a8-980c-0e12a9797be1
ms.openlocfilehash: 4bfb108e81f64ea368c6bcc846553eb1af5c23b1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792731"
---
# <a name="responsibilities-of-the-developer-in-overriding-default-behavior"></a>Responsabilidades do desenvolvedor em substituir o comportamento padrão
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]não impõe os seguintes requisitos, mas o comportamento será indefinido se esses requisitos não forem atendidos.  
  
- Substituindo o método não deve chamar <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ou <xref:System.Data.Linq.Table%601.Attach%2A>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]gera uma exceção se esses métodos são chamados em um método override.  
  
- Substituir métodos não pode ser usado para começar, confirmar, ou parar uma transação. A operação de <xref:System.Data.Linq.DataContext.SubmitChanges%2A> é executada em uma transação. Uma transação aninhada interna pode interferir com a transação externo. Os métodos de substituição de carregamento podem iniciar uma transação somente após determinar que a operação não estiver sendo executada em <xref:System.Transactions.Transaction>.  
  
- Os métodos de substituição deverão seguir o mapeamento aplicável de concorrência otimista. O método de substituição é esperado lançar <xref:System.Data.Linq.ChangeConflictException> quando um conflito de simultaneidade otimista ocorre. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]captura essa exceção para que você possa processar corretamente a <xref:System.Data.Linq.DataContext.SubmitChanges%2A> opção fornecida em. <xref:System.Data.Linq.DataContext.SubmitChanges%2A>  
  
- Crie (`Insert`) e métodos de substituição de `Update` são esperados fluir a voltar os valores para colunas base de dados - gerados correspondentes aos membros do objeto quando a operação é concluída com êxito.  
  
     Por exemplo, se `Order.OrderID` for mapeado para uma coluna de identidade (chave primária de*incremento automático* ) `InsertOrder()` , o método override deverá recuperar a ID gerada pelo banco de `Order.OrderID` dados e definir o membro para essa ID. Também, os membros de carimbo de data/hora devem ser atualizados para valores base de dados - gerados de carimbo de data/hora para certificar-se que os objetos atualizados são consistentes. A falha propagar os valores base de dados - gerados pode causar uma inconsistência entre o base de dados e objetos controlados por <xref:System.Data.Linq.DataContext>.  
  
- É responsabilidade do usuário chamar a API dinâmico correto. Por exemplo, o método de substituição de atualização, somente <xref:System.Data.Linq.DataContext.ExecuteDynamicUpdate%2A> pode ser chamado. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não detecta ou não verifica se o método dinâmico chamado corresponde a operação aplicável. Se um método inaplicável é chamado (por exemplo, <xref:System.Data.Linq.DataContext.ExecuteDynamicDelete%2A> para um objeto é atualizado), os resultados são indefinidos.  
  
- Finalmente, o método substituindo é esperado executar a operação indicada. A semântica de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] operações, como carregamento adiantado, carregamento adiado e <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) exigem as substituições para fornecer o serviço declarado. Por exemplo, uma substituição de carga que simplesmente retorna uma coleção vazia sem verificar o conteúdo no banco de dados provavelmente levará a um dado inconsistente.  
  
## <a name="see-also"></a>Consulte também

- [Personalizando as operações de inserção, atualização e exclusão](customizing-insert-update-and-delete-operations.md)
