---
title: Emitindo métodos e assemblies dinâmicos
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
ms.openlocfilehash: fda5a20eb7798086ec10415889454b4a8beba5f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180535"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a>Emitindo métodos e assemblies dinâmicos

Esta seção descreve um conjunto de tipos gerenciados no namespace <xref:System.Reflection.Emit> que permite que um compilador ou ferramenta emita metadados e o MSIL (Microsoft Intermediate Language) no tempo de execução e, opcionalmente, gere um arquivo executável portátil (PE) no disco. Mecanismos de script e compiladores são os principais usuários desse namespace. Nesta seção, a funcionalidade fornecida pelo namespace <xref:System.Reflection.Emit> é conhecida como emissão de reflexão.  
  
A emissão de reflexão fornece os seguintes recursos:  
  
- Defina métodos globais leves no tempo de execução usando a classe <xref:System.Reflection.Emit.DynamicMethod> e execute-os usando delegados.  
  
- Defina os assemblies no tempo de execução e, em seguida, execute-os e/ou salve-os em disco.  
  
- Defina os assemblies no tempo de execução, execute-os, descarregue-os e permita que a coleta de lixo recupere seus recursos.  
  
- Defina módulos em novos assemblies no tempo de execução e, em seguida, execute-os e/ou salve-os em disco.  
  
- Defina os tipos de módulos no tempo de execução, crie instâncias desses tipos e invoque seus métodos.  
  
- Identifique as informações simbólicas para módulos definidos que podem ser usadas por ferramentas como depuradores e criadores de perfil de código.  
  
Além dos tipos gerenciados no namespace <xref:System.Reflection.Emit>, há interfaces de metadados não gerenciados que são descritos na documentação de referência de [Interfaces de Metadados](../unmanaged-api/metadata/metadata-interfaces.md). A emissão de reflexão gerenciada fornece verificação de erros semânticos mais potente e um nível mais alto de abstração de metadados que as interfaces de metadados não gerenciadas.  
  
Outro recurso útil para trabalhar com metadados e MSIL é a documentação da CLI (Common Language Infrastructure), especialmente a “Partição II: definição e semântica de metadados” e a “Partição III: conjunto de instruções de CIL”. A documentação está disponível online no [site da Ecma.](https://www.ecma-international.org/publications/standards/Ecma-335.htm)  
  
## <a name="in-this-section"></a>Nesta seção
  
[Questões de segurança em reflexão emitidas](security-issues-in-reflection-emit.md)  
Descreve os problemas de segurança relacionados à criação de assemblies dinâmicos usando emissão de reflexão.  

[Como: Definir e executar métodos dinâmicos](how-to-define-and-execute-dynamic-methods.md) Mostra como executar um método dinâmico simples e um método dinâmico vinculado a uma instância de uma classe.

[Como: Definir um tipo genérico com reflexão emitida](how-to-define-a-generic-type-with-reflection-emit.md) Mostra como criar um tipo genérico simples com dois parâmetros de tipo, como aplicar classe, interface e restrições especiais aos parâmetros do tipo e como criar membros que usam os parâmetros de tipo da classe como tipos de parâmetros e tipos de retorno.

[Como: Definir um método genérico com reflexão emitida](how-to-define-a-generic-method-with-reflection-emit.md) Mostra como criar, emitir e invocar um método genérico simples.

[Montagens colecionáveis para geração de tipo dinâmico](collectible-assemblies.md) Introduz conjuntos colecionáveis, que são conjuntos dinâmicos que podem ser descarregados sem descarregar o domínio do aplicativo no qual foram criados.
  
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

[Reflexão](reflection.md)  
Explica como explorar os metadados e o código gerenciado.  
  
[Assemblies no .NET](../../standard/assembly/index.md)  
Fornece uma visão geral dos assemblies em implementações do .NET.
