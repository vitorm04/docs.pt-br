---
title: Estruturas de criação de perfil
ms.date: 03/30/2017
helpviewer_keywords:
- profiling structures [.NET Framework]
- unmanaged structures [.NET Framework], profiling
- structures [.NET Framework profiling]
ms.assetid: 750385f2-f365-41b1-939f-ca2f2ff9b466
ms.openlocfilehash: c3bbc66079e05abf494ad112b8aa0ac68e3c3e2f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868103"
---
# <a name="profiling-structures"></a>Estruturas de criação de perfil
Esta seção descreve as estruturas não gerenciadas que a API de perfil utiliza.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Estrutura COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md)  
 Fornece ao Common Language Runtime informações sobre um assembly de referência que deve ser considerado ao realizar um exame de fechamento de referência de assembly.  
  
 [Estrutura COR_PRF_CODE_INFO](cor-prf-code-info-structure.md)  
 Representa um bloco contíguo de código nativo armazenado na memória.  
  
 [Estrutura COR_PRF_EX_CLAUSE_INFO](cor-prf-ex-clause-info-structure.md)  
 Armazena informações sobre uma instância de cláusula de exceção específica e seu quadro associado.  
  
 [Estrutura COR_PRF_FUNCTION](cor-prf-function-structure.md)  
 Fornece uma representação única de uma função pela combinação de sua ID com a ID de sua versão recompilada.  
  
 [Estrutura COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md)  
 Representa os argumentos de uma função, em ordem da esquerda para a direita.  
  
 [Estrutura COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md)  
 Representa um bloco de argumentos de função armazenados de forma contígua em ordem da esquerda para a direita na memória.  
  
 [Estrutura COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md)  
 Descreve um intervalo (ou seja, um bloco) de memória que está passando por coleta de lixo.  
  
## <a name="related-sections"></a>Seções Relacionadas  
 COR_DEBUG_IL_TO_NATIVE_MAP  
  
 COR_IL_MAP  
  
 [Visão geral da criação de perfil](profiling-overview.md)  
  
 [Interfaces de criação de perfil](profiling-interfaces.md)  
  
 [Criando perfil de funções estáticas globais](profiling-global-static-functions.md)  
  
 [Criando perfil de enumerações](profiling-enumerations.md)
