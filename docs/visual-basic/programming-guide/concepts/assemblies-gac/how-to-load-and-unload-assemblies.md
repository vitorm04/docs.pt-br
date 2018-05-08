---
title: 'Como: carregar e descarregar Assemblies (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: bbc84236-04b6-4c1b-9672-52773f65a5dc
ms.openlocfilehash: 1cec7a7e15843874b65cf5d2f3a23b8e644a26d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
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
