---
ms.openlocfilehash: 9c2ee4ba66deb7c3b33698963add2b8a7e70069f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235116"
---
### <a name="intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a>Não é possível rolar intermitentemente para o item na parte inferior em ItemsControls (como ListBox e DataGrid) ao usar DataTemplates personalizados

|   |   |
|---|---|
|Detalhes|Em alguns casos, um bug no .NET Framework 4.5 está fazendo com que ItemsControls (como <xref:System.Windows.Controls.ListBox?displayProperty=name>, <xref:System.Windows.Controls.ComboBox?displayProperty=name>, <xref:System.Windows.Controls.DataGrid?displayProperty=name> etc.) não rolem para o item na parte inferior ao usar DataTemplates personalizados. Se houver uma tentativa de rolagem pela segunda vez (depois da rolagem de volta), ela funcionará.|
|Sugestão|Esse problema foi corrigido no .NET Framework 4.5.2 e pode ser solucionado com o upgrade para essa versão (ou uma versão posterior) do .NET Framework. Como alternativa, os usuários ainda podem arrastar as barras de rolagem para os itens finais nessas coleções, mas pode ser necessário tentar duas vezes para obter êxito.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Tempo de execução|
