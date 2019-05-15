---
title: Interoperabilidade COM em aplicativos .NET Framework (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
ms.openlocfilehash: 76c953941d2b8e7af5e4894fd1c521d62e64860f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65642119"
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a>Interoperabilidade COM em aplicativos .NET Framework (Visual Basic)

Quando você quiser usar objetos COM e objetos do .NET Framework no mesmo aplicativo, você precisa lidar com as diferenças em como os objetos existem na memória. Um objeto do .NET Framework está localizado na memória gerenciada — a memória controlada pelo common language runtime — e pode ser movido pelo tempo de execução, conforme necessário. Um objeto COM está localizado na memória não gerenciada e não é esperado para mover para outro local da memória. Visual Studio e o .NET Framework fornecem ferramentas para controlar a interação entre esses componentes gerenciados e não gerenciados. Para obter mais informações sobre o código gerenciado, consulte [Common Language Runtime](../../../standard/clr.md).

Além de usar objetos COM em aplicativos .NET, você talvez queira usar o Visual Basic para desenvolver objetos acessíveis a partir de código não gerenciado usando COM.

Os links nesta página fornecem detalhes sobre as interações entre os objetos COM e .NET Framework.

## <a name="related-sections"></a>Seções relacionadas

| | |
|---------|---------|
| [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md) | Fornece links para tópicos que abrangem a interoperabilidade COM em Visual Basic, incluindo COM objetos ActiveX controles, DLLs do Win32, os objetos gerenciados e herança de objetos COM. |
| [Interoperação com código não gerenciado](../../../framework/interop/index.md) | Descreve alguns dos problemas de interação entre código gerenciado e rapidamente e fornece links para estudar em mais detalhes. |
| [Wrappers COM](../../../framework/interop/com-wrappers.md) | Discute o runtime callable wrappers, que permitem que o código gerenciado chamar métodos COM, e COM callable wrappers, que permitem que os clientes COM chamar os métodos do objeto .NET. |
| [Interoperabilidade COM avançada](../../../framework/interop/index.md) | Fornece links para tópicos que abrangem a interoperabilidade de COM em relação aos wrappers, exceções, herança, threading, eventos, conversões e empacotamento. |
| [Tlbimp.exe (Importador de Biblioteca de Tipos)](../../../framework/tools/tlbimp-exe-type-library-importer.md) | Descreve a ferramenta que você pode usar para converter as definições de tipo encontradas dentro de uma biblioteca de tipos COM em definições equivalentes em um assembly do common language runtime. |
