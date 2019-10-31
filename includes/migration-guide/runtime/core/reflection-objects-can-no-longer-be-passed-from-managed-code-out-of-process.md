---
ms.openlocfilehash: d00f86c492a7d32344b1067a48c8e53aa2a43426
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858577"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a>Os objetos Reflection não podem mais ser passados de código gerenciado para clientes DCOM fora do processo

|   |   |
|---|---|
|Detalhes|Os objetos Reflection não podem mais ser passados de código gerenciado para clientes DCOM fora do processo. Os seguintes tipos são afetados:<ul><li><xref:System.Reflection.Assembly?displayProperty=name></li><li><xref:System.Reflection.MemberInfo?displayProperty=name> (e seus tipos derivados, incluindo <xref:System.Reflection.FieldInfo?displayProperty=name>, <xref:System.Reflection.MethodInfo?displayProperty=name>, <xref:System.Type?displayProperty=name> e <xref:System.Reflection.TypeInfo?displayProperty=name>)</li><li><xref:System.Reflection.MethodBody?displayProperty=name></li><li><xref:System.Reflection.Module?displayProperty=name></li><li><xref:System.Reflection.ParameterInfo?displayProperty=name>.</li></ul>Chamadas a <code>IMarshal</code> para o retorno do objeto <code>E_NOINTERFACE</code>.|
|Sugestão|Atualize o código de marshaling para trabalhar com objetos de não reflexão|
|Escopo|Secundário|
|Versão|4.6|
|Tipo|Tempo de execução|

