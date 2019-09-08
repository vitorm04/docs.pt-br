---
title: 'Simultaneidade otimista: Visão geral'
ms.date: 03/30/2017
ms.assetid: c2e38512-d0c8-4807-b30a-cb7e30338694
ms.openlocfilehash: fa7d423c0abc07e0d97f7d0d4d557aa11d675ee4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792930"
---
# <a name="optimistic-concurrency-overview"></a>Simultaneidade otimista: Visão geral
controle de simultaneidade otimista de suporte de[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . A tabela a seguir descreve os termos que se aplicam [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] à simultaneidade otimista na documentação do:  
  
|Termos|Descrição|  
|-----------|-----------------|  
|simultaneidade|A situação em que dois ou mais usuários tentarem ao mesmo tempo atualizar a mesma linha de base de dados.|  
|conflito de concorrência|A situação em que dois ou mais usuários tentarem ao mesmo tempo enviar conflitar valores em uma ou mais colunas de uma linha.|  
|controle de simultaneidade|A técnica usada para resolver conflitos de simultaneidade.|  
|controle de simultaneidade otimista|A técnica que investiga primeiro se outras transações alterados valores em uma linha antes de permitir alterações para ser enviada.<br /><br /> Compare com *controle de simultaneidade pessimista*, que bloqueia o registro para evitar conflitos de simultaneidade.<br /><br /> O controle *otimista* é tão chamado porque considera as chances de uma transação interferir com outra para ser improvável.|  
|resolução de conflitos|O processo de atualizar um item conflitante ver o base de dados novamente e depois reconciliar diferenças.<br /><br /> Quando um objeto é atualizado, o perseguidor de alteração de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] contém os seguintes dados:<br /><br /> -Os valores originalmente obtidos do banco de dados e usados para a verificação de atualização.<br />-Os novos valores de banco de dados da consulta subsequente.<br /><br /> em[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] determina se o objeto está em conflito (isto é, se um ou mais de seus valores de membros foram alterados). Se o objeto estiver em conflito, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] o próximo determina quais dos seus membros estão em conflito.<br /><br /> Qualquer conflito do membro que [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] descobrir é adicionado a uma lista de conflito.|  
  
 No modelo de objeto,umconflitodesimultaneidadeotimistaocorrequandoasduascondiçõesaseguirsão[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] verdadeiras:  
  
- Tentativas de cliente para enviar alterações para o base de dados.  
  
- Um ou mais valores de atualização- verificação foram atualizados na base de dados como o último de cliente os ler.  
  
 A resolução desse conflito inclui a descoberta de membros do objeto estão em conflito, e então decidir o que você deseja fazer sobre ele.  
  
> [!NOTE]
> Somente os membros mapeados como <xref:System.Data.Linq.Mapping.UpdateCheck.Always> ou <xref:System.Data.Linq.Mapping.UpdateCheck.WhenChanged> participam de verificação de simultaneidade otimista. Nenhuma verificação é executada para <xref:System.Data.Linq.Mapping.UpdateCheck.Never>marcado membros. Para obter mais informações, consulte <xref:System.Data.Linq.Mapping.UpdateCheck>.  
  
## <a name="example"></a>Exemplo  
 Por exemplo, o seguinte cenário, inicia User1 para preparar uma atualização ver o base de dados para uma linha. User1 recebe uma linha com valores de Alfreds, de Maria, e de vendas.  
  
 User1 deseja alterar o valor da coluna do gerenciador Alfred e o valor da coluna de departamento ao mercado. Antes que User1 pode enviar as alterações, Usuário2 alterações enviadas a base de dados. O valor da coluna assistente já foi alterado isso agora a Mary e o valor da coluna de departamento para atender.  
  
 Quando User1 agora tenta enviar alterações, o envio falha e de <xref:System.Data.Linq.ChangeConflictException> uma exceção é lançada. Este resultado ocorre porque os valores de base de dados para a coluna assistente e a coluna de departamento não são aqueles que foram esperadas. Os membros que representam as colunas do assistente e departamento estão em conflito. A tabela a seguir resume a situação.  
  
||Manager|Assistente|Departamento|  
|------|-------------|---------------|----------------|  
|Estado original|Alfreds|Maria|Vendas|  
|User1|Alfred||Marketing|  
|Usuário2||Mary|Serviço|  
  
 Você pode resolver conflitos como este de maneiras diferentes. Para obter mais informações, confira [Como: Gerenciar conflitos](how-to-manage-change-conflicts.md)de alterações.  
  
## <a name="conflict-detection-and-resolution-checklist"></a>Lista de verificação de detecção e de resolução de conflitos  
 Você pode detectar e resolver conflitos em qualquer nível de detalhe. Em um extremo, você pode resolver todos os conflitos em uma das três maneiras (consulte <xref:System.Data.Linq.RefreshMode>) sem consideração adicional. No extremo outro, você pode designar uma ação específica para cada tipo de conflito em cada membro em conflito.  
  
- Especificar ou revise as opções de <xref:System.Data.Linq.Mapping.UpdateCheck> no seu modelo de objeto.  
  
     Para obter mais informações, confira [Como: Especifique quais membros são testados para conflitos](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)de simultaneidade.  
  
- Em bloco try/catch de sua chamada a <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, especifique ponto em que você deseja exceções seja lançada.  
  
     Para obter mais informações, confira [Como: Especifique quando as exceções de simultaneidade são geradas](how-to-specify-when-concurrency-exceptions-are-thrown.md).  
  
- Determine quanto detalhes de conflito você deseja recuperar, e inclua código em seus bloco try/catch de acordo.  
  
     Para obter mais informações, confira [Como: Recupere informações](how-to-retrieve-entity-conflict-information.md) de conflitos de [entidade e como: Recuperar informações](how-to-retrieve-member-conflict-information.md)de conflito de membros.  
  
- Inclua no seu `try` /códigocomovocê desejaresolverosváriosconflitosquevocêdescobre`catch` .  
  
     Para obter mais informações, confira [Como: Resolva conflitos retendo os valores](how-to-resolve-conflicts-by-retaining-database-values.md)do banco de dados, [como: Resolva conflitos, substituindo valores](how-to-resolve-conflicts-by-overwriting-database-values.md)de banco de dados e [como: Resolva conflitos mesclando com valores](how-to-resolve-conflicts-by-merging-with-database-values.md)de banco de dados.  
  
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

- [Como: Gerenciar conflitos de alterações](how-to-manage-change-conflicts.md)
