---
title: 'Guia de migração para o .NET Framework 4.8, 4.7, 4.6 e 4.5 '
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
ms.openlocfilehash: fbaee646f7adcfe1a53d4231790e4258fd95a892
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102626"
---
# <a name="migrate-to-net-framework-48-47-46-and-45"></a>Migre para o Quadro .NET 4.8, 4.7, 4.6 e 4.5

Se você criou seu aplicativo usando uma versão anterior do .NET Framework, você geralmente pode atualizá-lo para o .NET Framework 4.5 e suas liberações de pontos (4.5.1 e 4.5.2), .NET Framework 4.6 e suas versões de pontos (4.6.1 e 4.6.2), .NET Framework 4.7 e suas versões de pontos (4.7.1 e 4.7.2) ou .NET Framework 4.8 facilmente. Abra o projeto no Visual Studio. Se o seu projeto tiver sido criado em uma versão anterior do Visual Studio, a caixa de diálogo **Compatibilidade do Projeto** abrirá automaticamente. Para saber mais sobre como atualizar um projeto no Visual Studio, consulte [Portar, migrar e atualizar projetos do Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) e [Direcionamento e compatibilidade da plataforma Visual Studio 2019](/visualstudio/releases/2019/compatibility).

 No entanto, algumas alterações no .NET Framework exigem alterações no seu código. Convém também aproveitar a nova funcionalidade no .NET Framework 4.5 e suas versões de correção, no .NET Framework 4.6 e suas versões de correção, no .NET Framework 4.7 e suas versões de correção ou no .NET Framework 4.8. Fazer esses tipos de alterações no seu aplicativo para uma nova versão do .NET Framework é tipicamente referido como *migração*. Se o seu aplicativo não tiver que ser migrado, você pode executá-lo no .NET Framework 4.5 ou em uma versão posterior sem recompilá-lo.

## <a name="migration-resources"></a>Recursos de migração

Revise os documentos a seguir antes de migrar seu aplicativo das versões anteriores do .NET Framework para a versão 4.5, 4.5.1, 4.5.2, 4.6.6, 4.6.2, 4.7, 4.7.1, 4.7.2 ou 4.8:

- Confira [Versões e dependências](versions-and-dependencies.md) para compreender a versão do CLR subjacente a cada versão do .NET Framework e examinar diretrizes para segmentação de seus aplicativos com êxito.

- Revise a [compatibilidade do aplicativo](application-compatibility.md) para saber sobre o tempo de execução e redirecionar as alterações que podem afetar seu aplicativo e como lidar com elas.

- Confira [O que está obsoleto na Biblioteca de Classes](../whats-new/whats-obsolete.md) para determinar todos os tipos ou membros no seu código que ficaram obsoletos e as alternativas recomendadas.

- Confira [Novidades](../whats-new/index.md) para obter descrições dos novos recursos que você talvez queira adicionar ao seu aplicativo.

## <a name="see-also"></a>Confira também

- [Compatibilidade de aplicativos](application-compatibility.md)
- [Migrar do .NET Framework 1.1](migrating-from-the-net-framework-1-1.md)
- [Compatibilidade de versão](version-compatibility.md)
- [Versões e Dependências](versions-and-dependencies.md)
- [Como: Configurar um aplicativo para suportar versões .NET Framework 4 ou posteriores](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Novidades](../whats-new/index.md)
- [O que está obsoleto na biblioteca de classes](../whats-new/whats-obsolete.md)
- [.NET Framework política de suporte oficial](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [Problemas de migração do .NET Framework 4](net-framework-4-migration-issues.md)
