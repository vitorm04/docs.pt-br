---
title: Interoperabilidade COM em aplicativos do .NET Framework (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 308ee8e495efa9368ef55d781f6b6dc314db51ac
ms.lasthandoff: 03/13/2017

---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a>Interoperabilidade COM em aplicativos .NET Framework (Visual Basic)
Quando você quiser usar objetos COM e .NET Framework no mesmo aplicativo, é necessário resolver as diferenças em como os objetos existem na memória. Um objeto do .NET Framework está localizado na memória gerenciada — a memória controlada pelo common language runtime — e pode ser movido pelo tempo de execução, conforme necessário. Um objeto COM está localizado na memória não gerenciada e não é esperado para mover para outro local da memória. [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]e o [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] fornecem ferramentas para controlar a interação dessas gerenciados e não gerenciados componentes. Para obter mais informações sobre o código gerenciado, consulte [Common Language Runtime](http://msdn.microsoft.com/library/059a624e-f7db-4134-ba9f-08b676050482).  
  
 Além de usar objetos COM em aplicativos .NET, você talvez queira usar [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] para desenvolver objetos acessíveis a partir do código não gerenciado usando COM.  
  
 Os links nesta página fornecem detalhes sobre as interações entre objetos COM e .NET Framework.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 Fornece links para tópicos que abrangem a interoperabilidade COM em Visual Basic, incluindo COM objetos ActiveX controles, as DLLs do Win32, os objetos gerenciados e herança de objetos COM.  
  
 [Erro de wrapper de interoperabilidade COM](https://docs.microsoft.com/cpp/misc/com-interop-wrapper-error)  
 Descreve as opções e as consequências se o sistema do projeto não é possível criar um wrapper de interoperabilidade COM para um componente específico.  
  
 [Interoperação com código não gerenciado](https://msdn.microsoft.com/library/sd10k43k)  
 Resumidamente descreve alguns dos problemas de interação entre código gerenciado e não gerenciado e fornece links para estudos adicionais.  
  
 [Wrappers COM](http://msdn.microsoft.com/library/e56c485b-6b67-4345-8e66-fd21835a6092)  
 Discute o runtime callable wrappers, que permitem ao código gerenciado chamar métodos COM, e callable wrappers COM, permitindo que clientes COM para chamar os métodos do objeto .NET.  
  
 [Interoperabilidade COM avançada](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 Fornece links para tópicos que abrangem a interoperabilidade de COM em relação ao wrappers, exceções, herança, threading, eventos, conversões e empacotamento.  
  
 [Tlbimp.exe (importador de biblioteca)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)  
 Descreve a ferramenta que você pode usar para converter as definições de tipo encontradas dentro de uma biblioteca de tipos COM em definições equivalentes em um assembly do common language runtime.
