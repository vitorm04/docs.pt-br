---
ms.openlocfilehash: 08c16f261338148619de2e484c73046b9d9a6bfe
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858386"
---
### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a>.NET Framework 4.6 não usa uma versão 4.5.x.x ao se registrar no registro

|   |   |
|---|---|
|Detalhes|Como é de se esperar, a chave de versão definida no registro (em <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) do .NET Framework 4.6 começa com "4.6", e não "4.5". Os aplicativos que dependem dessas chaves do Registro para saber quais versões do .NET Framework estão instaladas em um computador precisam ser atualizados para compreenderem que 4.6 é uma nova versão possível, compatível com as versões 4.5.x anteriores.|
|Sugestão|Atualize os aplicativos que estão investigando uma instalação do .NET Framework 4.5 procurando por chaves do Registro 4.5 que também aceitam 4.6.|
|Escopo|Microsoft Edge|
|Versão|4.6|
|Tipo|Tempo de execução|

