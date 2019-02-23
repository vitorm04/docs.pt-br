---
title: 'Como: Carregar e descarregar Assemblies (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: bbc84236-04b6-4c1b-9672-52773f65a5dc
ms.openlocfilehash: 77dc773c9e32c293ab5155b15e45f5255e31ab9a
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745205"
---
# <a name="how-to-load-and-unload-assemblies-visual-basic"></a>Como: Carregar e descarregar Assemblies (Visual Basic)
Os assemblies referenciados pelo seu programa serão automaticamente carregados e tempo de build, mas também é possível carregar assemblies específicos no domínio do aplicativo atual em tempo de execução. Para obter mais informações, confira [Como: Carregar assemblies em um domínio do aplicativo](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
 Não há nenhuma maneira de descarregar um assembly individual sem descarregar todos os domínios de aplicativo que o contêm. Mesmo se o assembly sair do escopo, o arquivo do assembly real permanecerá carregado até que todos os domínios do aplicativo que o contenham sejam descarregados.  
  
 Se você quiser descarregar alguns assemblies, mas não outros, considere criar um novo domínio do aplicativo, executando o código dentro desse domínio e descarregando esse domínio do aplicativo. Para obter mais informações, confira [Como: Descarregar um domínio do aplicativo](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>Para carregar um assembly em um domínio de aplicativo  
  
1.  Use um dos vários métodos de carga contidos nas classes <xref:System.AppDomain> e <xref:System.Reflection>. Para obter mais informações, confira [Como: Carregar assemblies em um domínio do aplicativo](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
### <a name="to-unload-an-application-domain"></a>Para descarregar um domínio de aplicativo  
  
1.  Não há nenhuma maneira de descarregar um assembly individual sem descarregar todos os domínios de aplicativo que o contêm. Use o método `Unload` de <xref:System.AppDomain> para descarregar os domínios de aplicativo. Para obter mais informações, confira [Como: Descarregar um domínio do aplicativo](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
## <a name="see-also"></a>Consulte também
- [Conceitos de Programação](../../../../visual-basic/programming-guide/concepts/index.md)
- [Assemblies no .NET](../../../../standard/assembly/index.md)
- [Como: Carregar assemblies em um domínio do aplicativo](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
