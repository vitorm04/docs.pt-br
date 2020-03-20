---
ms.openlocfilehash: fbc39b6e1cc19f6c2846caaabb9a8a721494b4e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67856985"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a>Permitir Unicode em URIs semelhantes a compartilhamentos UNC

|   |   |
|---|---|
|Detalhes|No <xref:System.Uri?displayProperty=fullName>, a criação de um URI de arquivo contendo um nome do compartilhamento UNC e caracteres Unicode não resultará mais em um URI com estado interno inválido. O comportamento será alterado somente quando todos os itens a seguir forem verdadeiros:<ul><li>O URI tiver o esquema <code>file:</code> e for seguido por quatro ou mais barras.</li><li>O nome do host começar com um sublinhado ou outro símbolo não reservado.</li><li>O URI contiver caracteres Unicode.</li></ul>|
|Sugestão|Os aplicativos que funcionam com URIs que contêm Unicode de forma consistente podem ter aceitado o uso desse comportamento para não permitir referências a compartilhamentos UNC. Esses aplicativos devem usar <xref:System.Uri.IsUnc>.|
|Escopo|Microsoft Edge|
|Versão|4.7.2|
|Type|Runtime|
|APIs afetadas|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|
