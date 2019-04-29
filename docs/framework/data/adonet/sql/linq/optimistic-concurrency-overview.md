---
title: 'Simultaneidade otimista: Visão geral'
ms.date: 03/30/2017
ms.assetid: c2e38512-d0c8-4807-b30a-cb7e30338694
ms.openlocfilehash: 8f3bd35cc1391339d99d5aa0a4021e29fa81756c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61767482"
---
# <a name="optimistic-concurrency-overview"></a>Simultaneidade otimista: Visão geral
controle de simultaneidade otimista de suporte de[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . A tabela a seguir descreve os termos que se aplicam a simultaneidade otimista em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentação:  
  
|Termos|Descrição|  
|-----------|-----------------|  
|simultaneidade|A situação em que dois ou mais usuários tentarem ao mesmo tempo atualizar a mesma linha de base de dados.|  
|conflito de concorrência|A situação em que dois ou mais usuários tentarem ao mesmo tempo enviar conflitar valores em uma ou mais colunas de uma linha.|  
|controle de simultaneidade|A técnica usada para resolver conflitos de simultaneidade.|  
|controle de simultaneidade otimista|A técnica que investiga primeiro se outras transações alterados valores em uma linha antes de permitir alterações para ser enviada.<br /><br /> Compare com *controle de simultaneidade pessimista*, que bloqueia o registro para evitar conflitos de simultaneidade.<br /><br /> *Otimista* controle é chamado porque então considera as chances de uma transação que interfere com outra para ser improvável.|  
|resolução de conflitos|O processo de atualizar um item conflitante ver o base de dados novamente e depois reconciliar diferenças.<br /><br /> Quando um objeto é atualizado, o perseguidor de alteração de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] contém os seguintes dados:<br /><br /> -Verifique os valores originalmente obtidas do banco de dados e usado para a atualização.<br />-Os novos valores de banco de dados de consulta subsequentes.<br /><br /> em[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] determina se o objeto está em conflito (isto é, se um ou mais de seus valores de membros foram alterados). Se o objeto está em conflito, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] em seguida, determina quais de seus membros estão em conflito.<br /><br /> Qualquer conflito do membro que [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] descobrir é adicionado a uma lista de conflito.|  
  
 No [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modelo de objeto, um *conflito de simultaneidade otimista* ocorre quando ambas das seguintes condições forem verdadeiras:  
  
- Tentativas de cliente para enviar alterações para o base de dados.  
  
- Um ou mais valores de atualização- verificação foram atualizados na base de dados como o último de cliente os ler.  
  
 A resolução desse conflito inclui a descoberta de membros do objeto estão em conflito, e então decidir o que você deseja fazer sobre ele.  
  
> [!NOTE]
>  Somente os membros mapeados como <xref:System.Data.Linq.Mapping.UpdateCheck.Always> ou <xref:System.Data.Linq.Mapping.UpdateCheck.WhenChanged> participam de verificação de simultaneidade otimista. Nenhuma verificação é executada para <xref:System.Data.Linq.Mapping.UpdateCheck.Never>marcado membros. Para obter mais informações, consulte <xref:System.Data.Linq.Mapping.UpdateCheck>.  
  
## <a name="example"></a>Exemplo  
 Por exemplo, o seguinte cenário, inicia User1 para preparar uma atualização ver o base de dados para uma linha. User1 recebe uma linha com valores de Alfreds, de Maria, e de vendas.  
  
 User1 deseja alterar o valor da coluna do gerenciador Alfred e o valor da coluna de departamento ao mercado. Antes que User1 pode enviar as alterações, Usuário2 alterações enviadas a base de dados. O valor da coluna assistente já foi alterado isso agora a Mary e o valor da coluna de departamento para atender.  
  
 Quando User1 agora tenta enviar alterações, o envio falha e de <xref:System.Data.Linq.ChangeConflictException> uma exceção é lançada. Este resultado ocorre porque os valores de base de dados para a coluna assistente e a coluna de departamento não são aqueles que foram esperadas. Os membros que representam as colunas do assistente e departamento estão em conflito. A tabela a seguir resume a situação.  
  
||Manager|Assistente|Departamento|  
|------|-------------|---------------|----------------|  
|Estado original|Alfreds|Maria|Vendas|  
|User1|Alfred||Marketing|  
|Usuário2||Mary|Serviço|  
  
 Você pode resolver conflitos como este de maneiras diferentes. Para obter mais informações, confira [Como: Gerenciar conflitos de alteração](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
## <a name="conflict-detection-and-resolution-checklist"></a>Lista de verificação de detecção e de resolução de conflitos  
 Você pode detectar e resolver conflitos em qualquer nível de detalhe. Em um extremo, você pode resolver todos os conflitos em uma das três maneiras (consulte <xref:System.Data.Linq.RefreshMode>) sem consideração adicional. No extremo outro, você pode designar uma ação específica para cada tipo de conflito em cada membro em conflito.  
  
- Especificar ou revise as opções de <xref:System.Data.Linq.Mapping.UpdateCheck> no seu modelo de objeto.  
  
     Para obter mais informações, confira [Como: Especificar quais membros são testados para conflitos de simultaneidade](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).  
  
- Em bloco try/catch de sua chamada a <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, especifique ponto em que você deseja exceções seja lançada.  
  
     Para obter mais informações, confira [Como: Especificar quando exceções de simultaneidade são geradas](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md).  
  
- Determine quanto detalhes de conflito você deseja recuperar, e inclua código em seus bloco try/catch de acordo.  
  
     Para obter mais informações, confira [Como: Recuperar informações de conflito de entidade](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-entity-conflict-information.md) e [como: Recuperar informações de conflito de membro](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-member-conflict-information.md).  
  
- Incluir em seu `try` / `catch` como você deseja resolver os conflitos que você descubra de código.  
  
     Para obter mais informações, confira [Como: Resolver conflitos mantendo valores de banco de dados](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md), [como: Resolver conflitos substituindo valores de banco de dados](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md), e [como: Resolver conflitos mesclando com valores de banco de dados](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-merging-with-database-values.md).  
  
## <a name="linq-to-sql-types-that-support-conflict-discovery-and-resolution"></a>Tipos LINQ to SQL que oferecem suporte a descoberta e a resolução de conflitos  
 As classes e os recursos para oferecer suporte a resolução de conflitos em concorrência otimista em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] incluem o seguinte:  
  
- <xref:System.Data.Linq.ObjectChangeConflict?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.MemberChangeConflict?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.ChangeConflictCollection?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.ChangeConflictException?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.DataContext.ChangeConflicts%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.DataContext.Refresh%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.Mapping.UpdateCheck?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.RefreshMode?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Consulte também

- [Como: Gerenciar conflitos de alteração](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
