---
title: Realizando marshaling em dados com interoperabilidade COM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
ms.assetid: 0bcdd7bf-5026-43eb-b08b-f03f90db9df9
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7e798f41f7c770fb0db0abf4a07e53cbaa6ccb40
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="marshaling-data-with-com-interop"></a>Realizando marshaling em dados com interoperabilidade COM
Interoperabilidade COM dá suporte ao uso de objetos COM por código gerenciado e à exposição de objetos gerenciados para COM. O suporte a marshaling dos dados de e para o COM é abrangente e quase sempre proporciona o comportamento de marshaling correto.  
  
 O [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] inclui as seguintes ferramentas de interoperabilidade COM:  
  
-   [Importador de biblioteca de tipos (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), que converte uma biblioteca de tipos COM para um assembly de interoperabilidade. Desse assembly, o serviço de marshaling de interoperabilidade gera wrappers que realizam marshaling entre memória gerenciada e não gerenciada.  
  
-   [Digite o exportador da biblioteca (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), que produz uma biblioteca de tipos COM de um assembly e gera um wrapper que realiza marshaling durante as chamadas de método.  
  
 Esta seção descreve os processos para personalizar os wrappers de interoperabilidade quando você pode (ou deve) fornecer informações de tipo adicionais ao marshaler.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Tipos de dados COM](http://msdn.microsoft.com/en-us/f93ae35d-a416-4218-8700-c8218cc90061)  
 Fornece tipos de dados gerenciados e não gerenciados correspondentes.  
  
 [Personalizando COM Callable Wrappers](http://msdn.microsoft.com/en-us/825177d3-4b2c-4723-82be-ce6ca2c34ace)  
 Descreve como realizar marshaling de tipos de dados explicitamente usando o atributo **MarshalAsAttribute** em tempo de design.  
  
 [Personalizando RCWs (Runtime Callable Wrappers)](http://msdn.microsoft.com/en-us/4652beaf-77d0-4f37-9687-ca193288c0be)  
 Descreve como ajustar o comportamento de marshaling de tipos em um assembly de interoperabilidade e como definir tipos COM manualmente.  
  
 [Como: migrar código DCOM gerenciado para o WCF](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 Descreve como migrar o código DCOM gerenciado para WCF para a solução mais segura.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Interoperabilidade COM avançada](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 Fornece links para obter mais informações sobre como incorporar componentes COM no aplicativo do .NET Framework.  
  
 [Resumo da conversão de assemblies em bibliotecas de tipos](http://msdn.microsoft.com/en-us/3a37eefb-a76c-4000-9080-7dbbf66a4896)  
 Descreve o processo de conversão de exportação de assembly em biblioteca de tipos.  
  
 [Resumo da conversão de bibliotecas de tipos em assemblies](http://msdn.microsoft.com/en-us/bf3f90c5-4770-4ab8-895c-3ba1055cc958)  
 Descreve o processo de conversão de importação de biblioteca de tipos em assembly.  
  
 [Interoperação usando tipos genéricos](http://msdn.microsoft.com/en-us/26b88e03-085b-4b53-94ba-a5a9c709ce58)  
 Descreve quais ações têm suporte ao usar tipos genéricos para interoperabilidade COM.

