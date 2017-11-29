---
title: Realizando marshaling em dados com interoperabilidade COM
ms.custom: 
ms.date: 09/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2def27790a1727bda524b8c14a93f7b78127a569
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="marshaling-data-with-com-interop"></a>Realizando marshaling em dados com interoperabilidade COM
Interoperabilidade COM dá suporte ao uso de objetos COM por código gerenciado e à exposição de objetos gerenciados para COM. O suporte a marshaling dos dados de e para o COM é abrangente e quase sempre proporciona o comportamento de marshaling correto.  
  
 O [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] inclui as seguintes ferramentas de interoperabilidade COM:  
  
-   [Importador de biblioteca de tipos (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), que converte uma biblioteca de tipos COM para um assembly de interoperabilidade. Desse assembly, o serviço de marshaling de interoperabilidade gera wrappers que realizam marshaling entre memória gerenciada e não gerenciada.  
  
-   [Digite o exportador da biblioteca (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), que produz uma biblioteca de tipos COM de um assembly e gera um wrapper que realiza marshaling durante as chamadas de método.  
  
 As seções a seguir links para tópicos que descrevem os processos para personalizar os wrappers de interoperabilidade quando você pode (ou deve) fornece o empacotador com informações de tipo adicionais.  
  
## <a name="in-this-section"></a>Nesta seção  
[Como: criar Wrappers manualmente](how-to-create-wrappers-manually.md)   
Descreve como criar um wrapper COM manualmente no código gerenciado. 
 
 [Como: migrar código DCOM gerenciado para o WCF](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 Descreve como migrar o código gerenciado do DCOM para o WCF para a solução mais segura.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Tipos de dados COM](https://msdn.microsoft.com/en-us/library/sak564ww(v=vs.100).aspx)  
 Fornece tipos de dados gerenciados e não gerenciados correspondentes.  
  
 [Personalizando COM Callable Wrappers](https://msdn.microsoft.com/en-us/library/3bwc828w(v=vs.100).aspx)  
 Descreve como realizar marshaling explicitamente os tipos de dados usando o <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributo em tempo de design.  
  
 [Personalizando RCWs (Runtime Callable Wrappers)](https://msdn.microsoft.com/en-us/library/e753eftz(v=vs.100).aspx)  
 Descreve como ajustar o comportamento de marshaling de tipos em um assembly de interoperabilidade e como definir tipos COM manualmente.  
  
 [Interoperabilidade COM avançada](https://msdn.microsoft.com/en-us/library/bd9cdfyx(v=vs.100).aspx)  
 Fornece links para obter mais informações sobre como incorporar componentes COM no aplicativo do .NET Framework.  
  
 [Resumo da conversão de assemblies em bibliotecas de tipos](https://msdn.microsoft.com/en-us/library/xk1120c3(v=vs.100).aspx)  
 Descreve o processo de conversão de exportação de assembly em biblioteca de tipos.  
  
 [Resumo da conversão de bibliotecas de tipos em assemblies](https://msdn.microsoft.com/en-us/library/k83zzh38(v=vs.100).aspx)  
 Descreve o processo de conversão de importação de biblioteca de tipos em assembly.  
  
 [Interoperação usando tipos genéricos](https://msdn.microsoft.com/en-us/library/ms229590(v=vs.100).aspx)  
 Descreve quais ações têm suporte ao usar tipos genéricos para interoperabilidade COM.
