---
title: Interoperabilidade COM em aplicativos .NET Framework (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
ms.openlocfilehash: ceef4255321e208911a16db0227890bc6654b8c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642909"
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a>Interoperabilidade COM em aplicativos .NET Framework (Visual Basic)
Quando você quiser usar objetos COM e objetos do .NET Framework no mesmo aplicativo, você deve considerar as diferenças em como os objetos existem na memória. Um objeto do .NET Framework está localizado na memória gerenciada — memória controlada pelo common language runtime — e podem ser movidos pelo tempo de execução, conforme necessário. Um objeto COM está localizado na memória não gerenciada e não é esperado para mover para outro local de memória. O Visual Studio e o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] fornecem ferramentas para controlar a interação entre eles gerenciados e componentes. Para obter mais informações sobre o código gerenciado, consulte [Common Language Runtime](../../../standard/clr.md).  
  
 Além de usar objetos COM em aplicativos .NET, você talvez queira usar o Visual Basic para desenvolver objetos de acesso do código não gerenciado usando COM.  
  
 Os links nesta página fornecem detalhes sobre as interações entre os objetos COM e .NET Framework.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 Fornece links para tópicos que abrangem a interoperabilidade COM em Visual Basic, incluindo COM objetos ActiveX controles, DLLs Win32, os objetos gerenciados e herança de objetos COM.  
  
 [Erro de wrapper de interoperabilidade COM](/cpp/misc/com-interop-wrapper-error)  
 Descreve as opções e as consequências se o sistema do projeto não é possível criar um wrapper de interoperabilidade COM para um componente específico.  
  
 [Interoperação com código não gerenciado](../../../framework/interop/index.md)  
 Brevemente descreve alguns dos problemas de interação entre o código gerenciado e não gerenciado e fornece links para estudar em mais detalhes.  
  
 [Wrappers COM](../../../framework/interop/com-wrappers.md)  
 Discute runtime callable wrappers do, que permitem que o código gerenciado chamar métodos COM, e callable wrappers COM, que permite que clientes COM chamar os métodos de objeto do .NET.  
  
 [Interoperabilidade COM avançada](../../../framework/interop/index.md)  
 Fornece links para tópicos que abrangem a interoperabilidade COM em relação ao wrappers, exceções, herança, threading, eventos, conversões e realização de marshaling.  
  
 [Tlbimp.exe (Importador de Biblioteca de Tipos)](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 Descreve a ferramenta que você pode usar para converter as definições de tipo encontradas dentro de uma biblioteca de tipos COM às definições equivalentes em um assembly do common language runtime.
