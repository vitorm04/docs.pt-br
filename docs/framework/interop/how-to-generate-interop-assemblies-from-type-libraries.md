---
title: Como gerar assemblies de interoperabilidade a partir de bibliotecas de tipos
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- Type Library Importer
- type libraries
- COM interop, importing type library
ms.assetid: 4afd40c3-68f2-41c5-8ec1-4951bc148b9c
ms.openlocfilehash: f4f099dfaf5ff02edd3958d7eab9354ce727a239
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74281796"
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a>Como gerar assemblies de interoperabilidade a partir de bibliotecas de tipos
O [Importador da Biblioteca de Tipos (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) é uma ferramenta de linha de comando que converte as classes e interfaces contidas em uma biblioteca de tipos COM em metadados. Essa ferramenta cria automaticamente um assembly de interoperabilidade e o namespace para as informações de tipo. Depois que os metadados de uma classe estiverem disponíveis, os clientes gerenciados podem criar instâncias do tipo COM e chamar os métodos dele, como se fosse uma instância do .NET. O Tlbimp.exe converte uma biblioteca de tipos inteira em metadados de uma só vez e não é capaz de gerar informações de tipo para um subconjunto dos tipos definidos em uma biblioteca de tipos.  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a>Para gerar um assembly de interoperabilidade de uma biblioteca de tipos  
  
1. Use o seguinte comando:  
  
     **tlbimp** \<*type-library-file*>  
  
     Adicionar a opção **/out:** produz um assembly de interoperabilidade com um nome alterado, como LOANLib.dll. A alteração do nome do assembly de interoperabilidade pode ajudar a diferenciá-lo da DLL COM original e evitar problemas que podem ocorrer devido a nomes duplicados.  
  
## <a name="example"></a>Exemplo  
 O comando a seguir produz o assembly Loanlib.dll no namespace `Loanlib`.  
  
```console  
tlbimp Loanlib.tlb  
```  
  
 O comando a seguir produz um assembly de interoperabilidade com um nome alterado (LOANLib.dll).  
  
```console  
tlbimp LoanLib.tlb /out: LOANLib.dll  
```  
  
## <a name="see-also"></a>Consulte também

- [Importando uma biblioteca de tipos como um assembly](importing-a-type-library-as-an-assembly.md)
- [Expondo componentes do COM ao .NET Framework](exposing-com-components.md)
