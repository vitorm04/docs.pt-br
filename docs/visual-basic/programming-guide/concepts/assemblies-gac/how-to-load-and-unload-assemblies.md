---
title: 'Como: carregar e descarregar Assemblies (Visual Basic) | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: bbc84236-04b6-4c1b-9672-52773f65a5dc
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 460d3a18fdee74c9b9c49ee465247b5b12d554d8
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-load-and-unload-assemblies-visual-basic"></a>Como: carregar e descarregar Assemblies (Visual Basic)
Os assemblies referenciados pelo seu programa será automaticamente carregados no momento da compilação, mas também é possível carregar assemblies específicos no domínio de aplicativo em tempo de execução. Para obter mais informações, consulte [como: carregar Assemblies em um domínio de aplicativo](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9).  
  
 Não há nenhuma maneira de descarregar um assembly individual sem descarregar todos os domínios de aplicativo que contêm-lo. Mesmo se o assembly sai do escopo, o arquivo de assembly real permanecerá carregado até que todos os domínios de aplicativo que contenham sejam descarregados.  
  
 Se você quiser descarregar alguns módulos (assemblies), mas outros não, considere criando um novo domínio de aplicativo, executar o código dentro desse domínio e, em seguida, o descarregamento desse domínio de aplicativo. Para obter mais informações, consulte [como: descarregar um domínio de aplicativo](http://msdn.microsoft.com/library/f356116d-e415-4f7c-a332-6e6a60227192).  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>Para carregar um assembly em um domínio de aplicativo  
  
1.  Use um dos vários métodos de carregamento contidos em classes <xref:System.AppDomain>e <xref:System.Reflection>.</xref:System.Reflection> </xref:System.AppDomain> Para obter mais informações, consulte [como: carregar Assemblies em um domínio de aplicativo](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9).  
  
### <a name="to-unload-an-application-domain"></a>Descarregar um domínio de aplicativo  
  
1.  Não há nenhuma maneira de descarregar um assembly individual sem descarregar todos os domínios de aplicativo que contêm-lo. Use o `Unload` método <xref:System.AppDomain>descarregar os domínios de aplicativo.</xref:System.AppDomain> Para obter mais informações, consulte [como: descarregar um domínio de aplicativo](http://msdn.microsoft.com/library/f356116d-e415-4f7c-a332-6e6a60227192).  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos de programação](../../../../visual-basic/programming-guide/concepts/index.md)   
 [Assemblies e o Cache de Assembly Global (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Como: carregar Assemblies em um domínio de aplicativo](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9)
