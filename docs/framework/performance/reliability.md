---
title: Confiabilidade
ms.date: 03/30/2017
helpviewer_keywords:
- SQL Server [.NET Framework]
- managed code, reliability
- reliability [.NET Framework]
- writing reliable code
- code, reliability
ms.assetid: 294aa306-0afe-4cbe-b397-86ba9f1860f8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b00ba0fdf732a864fb4fb757c6012a3d36740b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="reliability"></a>Confiabilidade
É importante que o código em execução em ambientes de servidor como o SQL Server proteja contra exceções assíncronas. A confiabilidade, conforme discutido aqui, não é específica para o SQL Server, mas sim para escrever código confiável para qualquer host executando em um ambiente do .NET Framework versão 2.0. No entanto, o SQL Server é o primeiro serviço fazendo uso amplo dos novos recursos de confiabilidade da versão 2.0, então ele é usado como exemplo.  
  
 Código em execução no SQL Server deve lidar com diretrizes de confiabilidade mais rígidas que as encontradas em outros ambientes de servidor. Isso ocorre devido à operação estável do SQL Server na borda de consumo de recursos.  Exceções <xref:System.OutOfMemoryException> e <xref:System.Threading.ThreadAbortException> não são incomuns no ambiente do SQL Server. Em linhas gerais, essas diretrizes concentram-se menos em confiabilidade e mais em permitir que código gerenciado totalmente confiável falhe de maneira elegante ao enfrentar uma reciclagem de nível de <xref:System.AppDomain>, que é a principal maneira pela qual o servidor mantém a consistência e a disponibilidade.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Programação em SQL Server e atributos de proteção de host](../../../docs/framework/performance/sql-server-programming-and-host-protection-attributes.md)  
 Descreve como o atributo <xref:System.Security.Permissions.HostProtectionAttribute> é usado pelo SQL Server para restringir a execução de código gerenciado.  
  
 [Melhores práticas de confiabilidade](../../../docs/framework/performance/reliability-best-practices.md)  
 Fornece diretrizes para escrever código que atende aos requisitos de confiabilidade.  
  
 [Regiões de execução restrita](../../../docs/framework/performance/constrained-execution-regions.md)  
 Descreve a função e o comportamento de CERs (regiões de execução restrita).  
  
## <a name="reference"></a>Referência  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
