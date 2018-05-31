---
title: Realizando marshaling em dados com interoperabilidade COM
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0d94223223568efe921af3a340815a966cc6c6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388349"
---
# <a name="marshaling-data-with-com-interop"></a>Realizando marshaling em dados com interoperabilidade COM
Interoperabilidade COM dá suporte ao uso de objetos COM por código gerenciado e à exposição de objetos gerenciados para COM. O suporte a marshaling dos dados de e para o COM é abrangente e quase sempre proporciona o comportamento de marshaling correto.  
  
 O [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] inclui as seguintes ferramentas de interoperabilidade COM:  
  
-   [Importador de biblioteca de tipos (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), que converte uma biblioteca de tipos COM para um assembly de interoperabilidade. Desse assembly, o serviço de marshaling de interoperabilidade gera wrappers que realizam marshaling entre memória gerenciada e não gerenciada.  
  
-   [Digite o exportador da biblioteca (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), que produz uma biblioteca de tipos COM de um assembly e gera um wrapper que realiza marshaling durante as chamadas de método.  
  
 As seções a seguir são vinculadas a tópicos que descrevem os processos para personalizar os wrappers de interoperabilidade quando você pode (ou precisa) fornecer informações de tipo adicionais ao marshaler.  
  
## <a name="in-this-section"></a>Nesta seção  
[Como criar wappers manualmente](how-to-create-wrappers-manually.md)   
Descreve como criar um wrapper COM manualmente no código-fonte gerenciado. 
 
 [Como: migrar código DCOM gerenciado para o WCF](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 Descreve como migrar o código DCOM gerenciado para o WCF para obter a solução mais segura possível.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Tipos de dados COM](https://msdn.microsoft.com/library/sak564ww(v=vs.100).aspx)  
 Fornece tipos de dados gerenciados e não gerenciados correspondentes.  
  
 [Personalizando COM Callable Wrappers](https://msdn.microsoft.com/library/3bwc828w(v=vs.100).aspx)  
 Descreve como realizar marshaling nos tipos de dados explicitamente usando o atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> em tempo de design.  
  
 [Personalizando RCWs (Runtime Callable Wrappers)](https://msdn.microsoft.com/library/e753eftz(v=vs.100).aspx)  
 Descreve como ajustar o comportamento de marshaling de tipos em um assembly de interoperabilidade e como definir tipos COM manualmente.  
  
 [Interoperabilidade COM avançada](https://msdn.microsoft.com/library/bd9cdfyx(v=vs.100).aspx)  
 Fornece links para obter mais informações sobre como incorporar componentes COM no aplicativo do .NET Framework.  
  
 [Resumo da conversão de assemblies em bibliotecas de tipos](https://msdn.microsoft.com/library/xk1120c3(v=vs.100).aspx)  
 Descreve o processo de conversão de exportação de assembly em biblioteca de tipos.  
  
 [Resumo da conversão de bibliotecas de tipos em assemblies](https://msdn.microsoft.com/library/k83zzh38(v=vs.100).aspx)  
 Descreve o processo de conversão de importação de biblioteca de tipos em assembly.  
  
 [Interoperação usando tipos genéricos](https://msdn.microsoft.com/library/ms229590(v=vs.100).aspx)  
 Descreve quais ações têm suporte ao usar tipos genéricos para interoperabilidade COM.
