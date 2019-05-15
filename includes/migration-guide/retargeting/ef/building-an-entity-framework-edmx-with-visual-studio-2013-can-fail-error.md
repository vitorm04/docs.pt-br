---
ms.openlocfilehash: ffafb0c9e3982dd168f907d32a8f59f96e6040d0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62087319"
---
### <a name="building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a>A compilação de um edmx do Entity Framework com o Visual Studio 2013 pode falhar com o erro MSB4062 se estiver usando as tarefas EntityDeploySplit ou EntityClean

|   |   |
|---|---|
|Detalhes|As ferramentas do MSBuild 12.0 (incluídas no Visual Studio 2013) alteraram os locais do arquivo MSBuild, fazendo com que arquivos de destino do Entity Framework sejam inválidos. O resultado é que as tarefas <code>EntityDeploySplit</code> e <code>EntityClean</code> falham porque não conseguem localizar <code>Microsoft.Data.Entity.Build.Tasks.dll</code>. Observe que essa interrupção se deve a uma alteração no conjunto de ferramentas (MSBuild/VS), e não por uma mudança no .NET Framework. Ela ocorrerá apenas no upgrade das ferramentas do desenvolvedor, não simplesmente no upgrade do .NET Framework.|
|Sugestão|Os arquivos de destino do Entity Framework foram corrigidos para trabalhar com o novo layout do MSBuild a partir do .NET Framework 4.6. O upgrade para essa versão do Framework corrigirá esse problema. Como alternativa, [esta solução alternativa](https://stackoverflow.com/a/24249247/131944) pode ser usada para aplicar patches diretamente aos arquivos de destino.|
|Escopo|Principal|
|Versão|4.5.1|
|Tipo|Redirecionando|
