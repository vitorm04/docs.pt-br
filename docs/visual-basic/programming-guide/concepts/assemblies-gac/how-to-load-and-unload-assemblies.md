---
title: 'Como: carregar e descarregar Assemblies (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbc84236-04b6-4c1b-9672-52773f65a5dc
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fd52a1094dba16c7e1bcba5bface9e13747cd4f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-load-and-unload-assemblies-visual-basic"></a>Como: carregar e descarregar Assemblies (Visual Basic)
Os assemblies referenciados pelo seu programa serão automaticamente carregados e tempo de build, mas também é possível carregar assemblies específicos no domínio do aplicativo atual em tempo de execução. Para obter mais informações, consulte [Como carregar assemblies em um domínio do aplicativo](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
 Não há nenhuma maneira de descarregar um assembly individual sem descarregar todos os domínios de aplicativo que o contêm. Mesmo se o assembly sair do escopo, o arquivo do assembly real permanecerá carregado até que todos os domínios do aplicativo que o contenham sejam descarregados.  
  
 Se você quiser descarregar alguns assemblies, mas não outros, considere criar um novo domínio do aplicativo, executando o código dentro desse domínio e descarregando esse domínio do aplicativo. Para obter mais informações, consulte [Como descarregar um domínio de aplicativo](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>Para carregar um assembly em um domínio de aplicativo  
  
1.  Use um dos vários métodos de carga contidos nas classes <xref:System.AppDomain> e <xref:System.Reflection>. Para obter mais informações, consulte [Como carregar assemblies em um domínio do aplicativo](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
### <a name="to-unload-an-application-domain"></a>Para descarregar um domínio de aplicativo  
  
1.  Não há nenhuma maneira de descarregar um assembly individual sem descarregar todos os domínios de aplicativo que o contêm. Use o método `Unload` de <xref:System.AppDomain> para descarregar os domínios de aplicativo. Para obter mais informações, consulte [Como descarregar um domínio de aplicativo](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos de Programação](../../../../visual-basic/programming-guide/concepts/index.md)  
 [Assemblies e o cache de assembly global (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Como carregar assemblies em um domínio do aplicativo](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
