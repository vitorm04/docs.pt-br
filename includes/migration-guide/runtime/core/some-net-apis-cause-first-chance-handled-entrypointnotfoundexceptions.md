---
ms.openlocfilehash: b23f06ec5b27fbd7976a4b62ba6105c607eaee39
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236679"
---
### <a name="some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a>Algumas APIs .NET causam EntryPointNotFoundExceptions de primeira chance

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.5, um pequeno número de métodos .NET começou a gerar <xref:System.EntryPointNotFoundException?displayProperty=name>s de primeira chance. Essas exceções eram tratadas dentro do .NET Framework, mas podiam interromper a automação de teste que não esperava as exceções de primeira instância. Essas mesmas APIs interrompem alguns cenários ApiVerifier quando HighVersionLie é habilitado.|
|Sugestão|Esse bug pode ser evitado com a o upgrade para o .NET Framework 4.5.1. Como alternativa, a automação de teste pode ser atualizada para não interromper <xref:System.EntryPointNotFoundException?displayProperty=name> de primeira chance.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.%23ctor(System.Type)?displayProperty=nameWithType></li></ul>|
