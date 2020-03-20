---
ms.openlocfilehash: 204fe32ec8b7fbaab89e37d7e761469212091728
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "68237913"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a>Contract.Invariant ou Contract.Requires\<TException> não consideram String.IsNullOrEmpty puro

|   |   |
|---|---|
|Detalhes|Para aplicativos que visam o .NET Framework 4.6.1, se o contrato invariante <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> para ou o contrato de pré-condição para <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> chamadas do <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> método, o reescritor emite aviso de compilador CC1036: &quot;Detected call to method 'System.String.IsNullOrWhteSpace(System.String)' sem [Pure] no método. &quot; Este é um aviso compilador em vez de um erro do compilador.|
|Sugestão|Esse comportamento foi abordado em [Problema nº 339 no GitHub](https://github.com/Microsoft/CodeContracts/issues/339). Para eliminar esse aviso, você pode baixar e compilar uma versão atualizada do código-fonte para a ferramenta de Contratos de Código no [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md). As informações para download são encontradas no fim da página.|
|Escopo|Secundária|
|Versão|4.6.1|
|Type|Runtime|
|APIs afetadas|<ul><li><xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType></li></ul>|
