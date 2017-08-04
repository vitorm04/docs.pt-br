---
title: "Guia de migração para o .NET Framework 4.7, 4.6 e 4.5 "
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
caps.latest.revision: 56
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 820d1966172a93c06c6451c51bc7f360496f46b8
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="migration-guide-to-the-net-framework-47-46-and-45"></a>Guia de migração para o .NET Framework 4.7, 4.6 e 4.5 
Se seu aplicativo foi criado usando uma versão anterior do .NET Framework, normalmente, você poderá atualizá-lo com facilidade para o .NET Framework 4.5 e suas versões pontuais (4.5.1 e 4.5.2), o .NET Framework 4.6 e suas versões pontuais (4.6.1 e 4.6.2) ou o .NET Framework 4.7. Abra seu projeto no Visual Studio. Se o seu projeto tiver sido criado em uma versão anterior, a caixa de diálogo **Compatibilidade do Projeto** abrirá automaticamente. Para saber mais sobre como atualizar um projeto no Visual Studio, veja [Portar, migrar e atualizar projetos do Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) e [Direcionamento e compatibilidade da plataforma Visual Studio 2017](https://www.visualstudio.com/en-us/productinfo/vs2017-compatibility-vs).  
  
 No entanto, algumas alterações feitas no .NET Framework exigem mudanças no seu código. Convém também aproveitar a nova funcionalidade no .NET Framework 4.5 e seus lançamentos pontuais, no .NET Framework 4.6 e seus lançamentos pontuais ou no .NET Framework 4.7. Fazer esses tipos de mudanças para seu aplicativo de uma nova versão do .NET Framework costuma ser conhecido como *migração*. Se o aplicativo não precisar ser migrado, é possível executar o .NET Framework 4.5 ou versões posteriores sem recompilá-lo.  
  
## <a name="migration-resources"></a>Recursos de migração  
 Revise os seguintes documentos antes de migrar seu aplicativo de versões anteriores do .NET Framework para a versão 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2 ou 4.7:  
  
-   Confira [Versões e dependências](../../../docs/framework/migration-guide/versions-and-dependencies.md) para compreender a versão do CLR subjacente a cada versão do .NET Framework e examinar diretrizes para segmentação de seus aplicativos com êxito.  
  
-   Confira [Compatibilidade de aplicativos](../../../docs/framework/migration-guide/application-compatibility.md) para saber mais sobre as alterações feitas no tempo de execução e no redirecionamento que podem afetar seu aplicativo e como lidar com eles.  
  
-   Confira [O que está obsoleto na Biblioteca de Classes](../../../docs/framework/whats-new/whats-obsolete.md) para determinar todos os tipos ou membros no seu código que ficaram obsoletos e as alternativas recomendadas.  
  
-   Confira [Novidades](../../../docs/framework/whats-new/index.md) para obter descrições dos novos recursos que você talvez queira adicionar ao seu aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Compatibilidade de aplicativos](../../../docs/framework/migration-guide/application-compatibility.md)   
 [Migrar do .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)   
 [Compatibilidade de versão](../../../docs/framework/migration-guide/version-compatibility.md)   
 [Versões e dependências](../../../docs/framework/migration-guide/versions-and-dependencies.md)   
 [Como configurar um aplicativo para oferecer suporte ao .NET Framework 4 ou 4.5](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)   
 [Novidades](../../../docs/framework/whats-new/index.md)   
 [O que está obsoleto na Biblioteca de Classes](../../../docs/framework/whats-new/whats-obsolete.md)   
 [Versão do .NET Framework e informações de Assembly](http://go.microsoft.com/fwlink/?LinkId=201701)   
 [Política de ciclo de vida de suporte do Microsoft .NET Framework](http://go.microsoft.com/fwlink/?LinkId=196607) [Problemas de migração do .NET Framework 4](net-framework-4-migration-issues.md)

