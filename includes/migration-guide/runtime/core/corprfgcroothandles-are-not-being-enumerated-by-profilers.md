---
ms.openlocfilehash: 8dc98b2d9c2c0b5f145ebce48cf8f5e054975c6e
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858576"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a>COR_PRF_GC_ROOT_HANDLEs não estão sendo enumerados por criadores de perfil

|   |   |
|---|---|
|Detalhes|No .NET Framework v4.5.1, a API de criação de perfil <code>RootReferences2()</code>, de maneira incorreta, nunca retorna <code>COR_PRF_GC_ROOT_HANDLE</code> (que, em vez disso, é retornada como <code>COR_PRF_GC_ROOT_OTHER</code>). Esse problema foi corrigido a partir do .NET Framework 4.6.|
|Sugestão|Esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.|
|Escopo|Secundário|
|Versão|4.5.1|
|Tipo|Tempo de execução|

