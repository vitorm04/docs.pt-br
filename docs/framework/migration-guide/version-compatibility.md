---
title: Compatibilidade de versão no .NET Framework
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
ms.openlocfilehash: c3e2368bc5977d7f50ae7ecea8557c5c545e82a4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73455599"
---
# <a name="version-compatibility-in-the-net-framework"></a>Compatibilidade de versão no .NET Framework

Compatibilidade com versões anteriores significa que um aplicativo desenvolvido para uma versão específica de uma plataforma será executado em versões posteriores dessa plataforma. O .NET Framework tenta maximizar a compatibilidade com versões anteriores: o código-fonte gravado para uma versão do .NET Framework deve compilar em versões posteriores do .NET Framework e os binários executados em uma versão do .NET Framework devem se comportar de forma idêntica em versões posteriores do .NET Framework.

## <a name="Apps"></a> Compatibilidade de versão para aplicativos

Por padrão, um aplicativo executado na versão do .NET Framework para o qual foi compilado. Se essa versão não estiver presente e o arquivo de configuração de aplicativos não definir versões compatíveis, um erro de inicialização do .NET Framework poderá ocorrer. Nesse caso, a tentativa de executar o aplicativo falhará.

Para definir as versões específicas nas quais seu aplicativo é executado, adicione um ou mais elementos [\<supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) ao arquivo de configuração de aplicativo. Cada elemento `<supportedRuntime>` lista uma versão compatível do runtime, com o primeiro especificando a versão mais preferida e o último especificando a versão menos preferida.

```xml
<configuration>
   <startup>
      <supportedRuntime version="v2.0.50727" />
      <supportedRuntime version="v4.0" />
   </startup>
</configuration>
```

Para saber mais, confira [How to: Configure an App to Support .NET Framework 4 or 4.x](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md) (Como configurar um aplicativo para dar suporte ao .NET Framework 4 ou 4.x).

## <a name="version-compatibility-for-components"></a>Compatibilidade de versão para componentes

Um aplicativo pode controlar a versão do .NET Framework no qual é executado, mas um componente não pode. Os componentes e as bibliotecas de classe são carregados no contexto de um aplicativo específico e é por isso que são executados automaticamente na versão do .NET Framework em que o aplicativo é executado.

Por conta dessa restrição, as garantias de compatibilidade são especialmente importante para componentes. Desde o .NET Framework 4, você pode especificar o grau em que um componente deve permanecer compatível em várias versões aplicando o atributo <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=nameWithType> ao componente. As ferramentas podem usar esse atributo para detectar potenciais violações da garantia de compatibilidade em futuras versões de um componente.

## <a name="backward-compatibility-and-the-net-framework"></a>Compatibilidade com versões anteriores e o .NET Framework

O .NET Framework 4.5 e as versões posteriores são compatíveis com versões anteriores de aplicativos que foram compilados com versões anteriores do .NET Framework. Em outras palavras, aplicativos e componentes compilados com versões anteriores funcionarão sem modificação no .NET Framework 4.5 e versões posteriores. No entanto, por padrão, como os aplicativos são executados na versão do Common Language Runtime para a qual foram desenvolvidos, talvez você precise fornecer um arquivo de configuração para permitir que seu aplicativo seja executado no .NET Framework 4.5 ou versões posteriores. Para saber mais, confira a seção [Compatibilidade de versão para aplicativos](#Apps), anteriormente neste artigo.

Na prática, essa compatibilidade pode ser desfeita por alterações aparentemente inconsequentes feitas no .NET Framework e por alterações em técnicas de programação. Por exemplo, as melhorias de desempenho no .NET Framework 4.5 podem expor uma condição de corrida que não ocorria em versões anteriores. Da mesma forma, o uso de um caminho codificado para assemblies do .NET Framework, a execução de uma comparação de igualdade com uma versão específica do .NET Framework e a obtenção do valor de um campo particular usando-se reflexão não são práticas compatíveis com versões anteriores. Além disso, cada versão do .NET Framework inclui correções de bug e mudanças relacionadas à segurança que podem afetar a compatibilidade de alguns aplicativos e componentes.

Se o aplicativo ou o componente não funcionar conforme esperado no .NET Framework 4.5 (incluindo suas versões de ponto, o .NET Framework 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 ou 4.8), use as seguintes listas de verificação:

- Se seu aplicativo foi desenvolvido para ser executado em qualquer versão do .NET Framework a partir do .NET Framework 4,0, consulte [compatibilidade de aplicativos](application-compatibility.md) para gerar listas de alterações entre sua versão de .NET Framework de destino e a versão na qual seu aplicativo está sendo executado.

- Se você tiver um aplicativo .NET Framework 3.5, consulte também [Problemas de migração do .NET Framework 4](../migration-guide/net-framework-4-migration-issues.md).

- Se você tiver um aplicativo .NET Framework 2.0, consulte também [Alterações no .NET Framework 3.5 SP1](https://go.microsoft.com/fwlink/?LinkId=186989).

- Se você tiver um aplicativo .NET Framework 1.1, consulte também [Alterações no .NET Framework 2.0](https://go.microsoft.com/fwlink/?LinkID=125263).

- Caso esteja recompilando o código-fonte existente para ser executado no .NET Framework 4.5 ou suas versões de ponto ou desenvolvendo uma nova versão de um aplicativo ou componente direcionado ao .NET Framework 4.5 ou suas versões de ponto de uma base de código-fonte existente, confira [O que está obsoleto na biblioteca de classes](../whats-new/whats-obsolete.md) para obter tipos e membros obsoletos e aplicar a solução alternativa descrita. (O código compilado anteriormente continuará sendo executado em tipos e membros marcados como obsoletos.)

- Se você determinar que uma alteração no .NET Framework 4.5 interrompeu seu aplicativo, confira o [Esquema de configurações de runtime](../configure-apps/file-schema/runtime/index.md) e, em especial, [\<AppContextSwitchOverrides&gt; Element](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), para determinar se é possível usar uma configuração de runtime em seu arquivo de configuração de aplicativo para restaurar o comportamento anterior.

- Se você encontrar um problema que não está documentado, abra um problema no [site da Comunidade de Desenvolvedores do .NET](https://developercommunity.visualstudio.com/spaces/61/index.html) ou no [repositório GitHub do Microsoft/dotnet](https://github.com/microsoft/dotnet/issues).

## <a name="compatibility-and-side-by-side-execution"></a>Compatibilidade e execução lado a lado

Se você não conseguir encontrar uma solução alternativa adequada para seu problema, lembre-se de que o .NET Framework 4.5 (ou uma de suas versões pontuais) é executado lado a lado com as versões 1.1, 2.0 e 3.5, além de ser uma atualização in-loco que substitui a versão 4. Para aplicativos que segmentam as versões 1.1, 2.0 e 3.5, é possível instalar a versão do .NET Framework adequada no computador de destino para executar o aplicativo em seu melhor ambiente. Para saber mais sobre a execução lado a lado, confira [Side-by-Side Execution](../deployment/side-by-side-execution.md) (Execução lado a lado).

## <a name="see-also"></a>Consulte também

- [Novidades](../whats-new/index.md)
- [O que está obsoleto na Biblioteca de Classes](../whats-new/whats-obsolete.md)
- [Compatibilidade de aplicativos](../migration-guide/application-compatibility.md)
- [Política de ciclo de vida de suporte do Microsoft .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=248212)
- [Problemas de migração do .NET Framework 4](../migration-guide/net-framework-4-migration-issues.md)
