---
ms.openlocfilehash: d3c6818861f8b0261a9a71a4654029143d928d08
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760710"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a>Permitir Unicode em URIs semelhantes a compartilhamentos UNC

|   |   |
|---|---|
|Detalhes|No <xref:System.Uri?displayProperty=fullName>, a criação de um URI de arquivo contendo um nome do compartilhamento UNC e caracteres Unicode não resultará mais em um URI com estado interno inválido. O comportamento será alterado somente quando todos os itens a seguir forem verdadeiros:<ul><li>O URI tiver o esquema <code>file:</code> e for seguido por quatro ou mais barras.</li><li>O nome do host começar com um sublinhado ou outro símbolo não reservado.</li><li>O URI contiver caracteres Unicode.</li></ul>|
|Sugestão|Os aplicativos que funcionam com URIs que contêm Unicode de forma consistente podem ter aceitado o uso desse comportamento para não permitir referências a compartilhamentos UNC. Esses aplicativos devem usar <xref:System.Uri.IsUnc>.|
|Escopo|Microsoft Edge|
|Versão|4.7.2|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|

