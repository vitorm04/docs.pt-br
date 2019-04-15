---
ms.openlocfilehash: 3f553f95941eaf36cf335e9765a670a05bd157f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234088"
---
### <a name="appdomainsetupdynamicbase-is-no-longer-randomized-by-userandomizedstringhashalgorithm"></a>AppDomainSetup.DynamicBase não é mais randomizado por UseRandomizedStringHashAlgorithm

|   |   |
|---|---|
|Detalhes|Antes do .NET Framework 4.6, o valor de <xref:System.AppDomainSetup.DynamicBase> seria randomizado entre domínios de aplicativos ou entre processos se UseRandomizedStringHashAlgorithm estivesse habilitado no arquivo de configuração do aplicativo. A partir do .NET Framework 4.6, <xref:System.AppDomainSetup.DynamicBase> retornará um resultado estável entre instâncias diferentes de um aplicativo em execução e entre diferentes domínios de aplicativo. Bases dinâmicas ainda serão diferentes para diferentes aplicativos. Essa alteração remove apenas o elemento de nomenclatura aleatório para instâncias diferentes do mesmo aplicativo.|
|Sugestão|Lembre-se de que habilitar <code>UseRandomizedStringHashAlgorithm</code> não fará com que <xref:System.AppDomainSetup.DynamicBase> seja randomizado. Se for necessária uma base aleatória, ela deverá ser produzida no código do aplicativo, e não por meio dessa API.|
|Escopo|Microsoft Edge|
|Versão|4.6|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.AppDomainSetup.DynamicBase?displayProperty=nameWithType></li></ul>|
