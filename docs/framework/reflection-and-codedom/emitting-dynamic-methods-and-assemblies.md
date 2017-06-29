---
title: "Emitindo métodos e assemblies dinâmicos | Microsoft Docs"
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
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
ms.assetid: 8e8e2631-62fd-40e7-a8ee-0039b06749bc
caps.latest.revision: 18
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d8e4c5bb677be7e20f6571ea6eb53831027ade27
ms.contentlocale: pt-br
ms.lasthandoff: 06/02/2017

---
# <a name="emitting-dynamic-methods-and-assemblies"></a>Emitindo métodos e assemblies dinâmicos
Esta seção descreve um conjunto de tipos gerenciados no namespace <xref:System.Reflection.Emit> que permite que um compilador ou ferramenta emita metadados e o MSIL (Microsoft Intermediate Language) no tempo de execução e, opcionalmente, gere um arquivo executável portátil (PE) no disco. Mecanismos de script e compiladores são os principais usuários desse namespace. Nesta seção, a funcionalidade fornecida pelo namespace <xref:System.Reflection.Emit> é conhecida como emissão de reflexão.  
  
 A emissão de reflexão fornece os seguintes recursos:  
  
-   Defina métodos globais leves no tempo de execução usando a classe <xref:System.Reflection.Emit.DynamicMethod> e execute-os usando delegados.  
  
-   Defina os assemblies no tempo de execução e, em seguida, execute-os e/ou salve-os em disco.  
  
-   Defina os assemblies no tempo de execução, execute-os, descarregue-os e permita que a coleta de lixo recupere seus recursos.  
  
-   Defina módulos em novos assemblies no tempo de execução e, em seguida, execute-os e/ou salve-os em disco.  
  
-   Defina os tipos de módulos no tempo de execução, crie instâncias desses tipos e invoque seus métodos.  
  
-   Identifique as informações simbólicas para módulos definidos que podem ser usadas por ferramentas como depuradores e criadores de perfil de código.  
  
 Além dos tipos gerenciados no namespace <xref:System.Reflection.Emit>, há interfaces de metadados não gerenciados que são descritos na documentação de referência de [Interfaces de Metadados](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md). A emissão de reflexão gerenciada fornece verificação de erros semânticos mais potente e um nível mais alto de abstração de metadados que as interfaces de metadados não gerenciadas.  
  
 Outro recurso útil para trabalhar com metadados e MSIL é a documentação da CLI (Common Language Infrastructure), especialmente a “Partição II: definição e semântica de metadados” e a “Partição III: conjunto de instruções de CIL”. A documentação está disponível online no [MSDN](http://go.microsoft.com/fwlink/?LinkID=65555) e no [site da Ecma](http://go.microsoft.com/fwlink/?LinkId=116487).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Problemas de segurança na emissão de reflexão](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
 Descreve os problemas de segurança relacionados à criação de assemblies dinâmicos usando emissão de reflexão.  
  
## <a name="reference"></a>Referência  
 <xref:System.Reflection.Emit.OpCodes>  
 Cataloga os códigos de instrução de MSIL, que você pode usar para criar corpos de método.  
  
 <xref:System.Reflection.Emit>  
 Contém classes gerenciadas usadas para emitir métodos, assemblies e tipos dinâmicos.  
  
 <xref:System.Type>  
 Descreve a classe <xref:System.Type>, que representa os tipos de reflexão gerenciada e emissão de reflexão, e qual é a chave para o uso dessas tecnologias.  
  
 <xref:System.Reflection>  
 Contém classes gerenciadas usadas para explorar os metadados e o código gerenciado.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Reflexão](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Explica como explorar os metadados e o código gerenciado.  
  
 [Assemblies no Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Fornece uma visão geral dos assemblies no .NET Framework.
