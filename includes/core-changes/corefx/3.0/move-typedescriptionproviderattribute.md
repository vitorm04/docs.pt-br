---
ms.openlocfilehash: 57ca2ad839aab8d61da1a929660920efe1190334
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147530"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a>TypeDescriptionProviderAttribute movido para outro conjunto

A <xref:System.ComponentModel.TypeDescriptionProviderAttribute> classe foi movida.

#### <a name="change-description"></a>Descrição da alteração

Nas versões .NET Core 2.2 e anteriores, a <xref:System.ComponentModel.TypeDescriptionProviderAttribute> classe é encontrada no conjunto *System.ComponentModel.TypeConverter.*

A partir do .NET Core 3.0, ele é encontrado no conjunto *System.ObjectModel.*

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="recommended-action"></a>Ação recomendada

Essa alteração afeta apenas aplicativos que usam <xref:System.ComponentModel.TypeDescriptionProviderAttribute> reflexão para carregar <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> o tipo <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> chamando um método como ou uma sobrecarga que assume que o tipo está em um conjunto específico. Se esse for o caso, a montagem referenciada na chamada do método deve ser atualizada para refletir o novo local de montagem do tipo.

#### <a name="category"></a>Categoria

Windows Forms

#### <a name="affected-apis"></a>APIs afetadas

Nenhum.

<!--

### Affected APIs

- Not detectable via API analysis

-->
