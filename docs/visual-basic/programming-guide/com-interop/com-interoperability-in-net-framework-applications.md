---
title: "Interoperabilidade COM em aplicativos .NET Framework (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "interoperabilidade COM"
  - "interoperabilidade, objetos COM e .NET Framework"
  - "componentes compartilhados"
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Interoperabilidade COM em aplicativos .NET Framework (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Quando você deseja usar objetos COM e.Objetos do NET Framework no mesmo aplicativo, você precisa lidar com as diferenças em como os objetos existem na memória.  R.Objeto do NET Framework está localizado na memória gerenciada — memória controlada pelo common language runtime — e pode ser movida pelo runtime conforme necessário.  Um objeto COM está localizado na memória não gerenciada e não é esperado para mover para outro local de memória.  [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]e o [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] fornecem ferramentas para controlar a interação deles e gerenciados de componentes.  Para obter mais informações sobre o código gerenciado, consulte [Common Language Runtime](../Topic/Common%20Language%20Runtime%20\(CLR\).md).  
  
 Além de ser usado COM objetos no.NET applications, você também poderá usar [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] para desenvolver os objetos acessíveis a partir do código não gerenciado usando com.  
  
 Os links nesta página fornecem detalhes sobre as interações entre COM e.Objetos do NET Framework.  
  
## Seções relacionadas  
 [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 Fornece links para tópicos abrangendo a interoperabilidade COM em Visual Basic, inclusive COM objetos, ActiveX controles, DLLs Win32, os objetos gerenciados e herança de objetos COM.  
  
 [Erro de wrapper de interoperabilidade COM](/visual-cpp/misc/com-interop-wrapper-error)  
 Descreve as opções e as conseqüências se o sistema do projeto não é possível criar um wrapper de interoperabilidade COM para um componente específico.  
  
 [Interoperação com código não gerenciado](../Topic/Interoperating%20with%20Unmanaged%20Code.md)  
 Forneça uma breve descreve alguns dos problemas de interação entre código gerenciado e e fornece links para estudos adicionais.  
  
 [Wrappers COM](../Topic/COM%20Wrappers.md)  
 Discute runtime callable wrappers, que permitem código gerenciado chamar métodos COM, e COM callable wrappers, permitindo que os clientes COM a chamada.Métodos do objeto NET.  
  
 [Advanced COM Interoperability](http://msdn.microsoft.com/pt-br/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 Fornece links para tópicos que abordam a interoperabilidade COM relação a invólucros, exceções, herança, threading, eventos, conversões e empacotamento.  
  
 [Tlbimp.exe \(Importador de Biblioteca de Tipos\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md)  
 Discute a ferramenta que você pode usar para converter as definições de tipo encontradas dentro de uma biblioteca de tipos COM em definições equivalentes em um assembly de tempo de execução de linguagem comum.