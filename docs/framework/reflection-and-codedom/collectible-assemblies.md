---
title: "Assemblies de coleção para a geração de tipo dinâmico"
description: 
ms.date: 08/29/2017
ms.prod: .net
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reflection, dynamic assembly
- assemblies, collectible
- collectible assemblies, retrieving
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2c9a613f4cc13c3e4189a59ace2e05d01d1bcb4f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="collectible-assemblies-for-dynamic-type-generation"></a>Assemblies de coleção para a geração de tipo dinâmico

*Assemblies de coleção* são assemblies dinâmicos que podem ser baixados sem descarregar o domínio de aplicativo no qual eles foram criados. Pode ser recuperada toda gerenciada e a memória usada por um assembly de coleção e os tipos que ele contém. Informações como o nome do assembly são removidas das tabelas internas.

Para habilitar o descarregamento, use o <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType> sinalizador quando você cria um assembly dinâmico. O assembly é transitório (isto é, ele não pode ser salvo) e está sujeita às limitações descritas no [restrições em Assemblies de coleção](#restrictions-on-collectible-assemblies) seção. O common language runtime (CLR) descarrega um assembly de coleção automaticamente quando você liberar todos os objetos associados ao assembly. Em todos os outros aspectos, os assemblies de coleção são criados e usados da mesma maneira como outros assemblies dinâmicos.

## <a name="lifetime-of-collectible-assemblies"></a>Tempo de vida de assemblies de coleção

O tempo de vida de um assembly de coleção é controlado pela existência de referências para os tipos que ele contém e os objetos que são criados a partir desses tipos. O common language runtime não descarregar um assembly como um ou mais dos seguintes existe (`T` é qualquer tipo que é definido no assembly): 

- Uma instância de `T`.

- Uma instância de uma matriz de `T`.
 
- Uma instância de um tipo genérico que tenha `T` como um de seus argumentos de tipo. Isso inclui coleções genéricas do `T`, mesmo se a coleção está vazia.

- Uma instância de <xref:System.Type> ou <xref:System.Reflection.Emit.TypeBuilder> que representa `T`. 

   > [!IMPORTANT]
   > Você deve liberar todos os objetos que representam as partes do assembly. O <xref:System.Reflection.Emit.ModuleBuilder> que define `T` mantém uma referência para o <xref:System.Reflection.Emit.TypeBuilder>e o <xref:System.Reflection.Emit.AssemblyBuilder> objeto mantém uma referência para o <xref:System.Reflection.Emit.ModuleBuilder>, portanto, as referências a esses objetos devem ser liberadas. Até mesmo a existência de um <xref:System.Reflection.Emit.LocalBuilder> ou um <xref:System.Reflection.Emit.ILGenerator> usada na construção de `T` impede descarregar.

- Uma referência estática a `T` por outro tipo definido de forma dinâmica `T1` que é ainda pode ser acessado pelo código em execução. Por exemplo, `T1` podem derivar de `T`, ou `T` pode ser o tipo de um parâmetro em um método de `T1`.
 
- Um **ByRef** para um campo estático que pertence a `T`.

- Um <xref:System.RuntimeTypeHandle>, <xref:System.RuntimeFieldHandle>, ou <xref:System.RuntimeMethodHandle> que se refere a `T` ou a um componente de `T`.

- Uma instância de qualquer objeto de reflexão que pode ser usado indiretamente ou diretamente para acessar o <xref:System.Type> objeto que representa `T`. Por exemplo, o <xref:System.Type> de objeto para `T` pode ser obtido de um tipo de matriz cujo tipo de elemento é `T`, ou de um tipo genérico que tenha `T` como um argumento de tipo. 

- Um método `M` na pilha de chamadas de qualquer thread, onde `M` é um método de `T` ou um método de nível de módulo é definido no assembly.

- Um delegado a um método estático que é definido em um módulo do assembly.

Se houver um item da lista para apenas um tipo ou um método no assembly, apenas o tempo de execução não é possível descarregar o assembly.

> [!NOTE]
> O tempo de execução não descarregar, na verdade, o assembly até finalizadores executar para todos os itens na lista.

Para fins de controle de tempo de vida, um construído tipo genérico, como `List<int>` (em c#) ou `List(Of Integer)` (no Visual Basic), que é criado e usado na geração de um assembly de coleção é considerada como tendo sido definido no assembly que contém o genérico definição de tipo ou em um assembly que contém a definição de um de seus argumentos de tipo. O conjunto exato usado é um detalhe de implementação e sujeito a alterações.
 
## <a name="restrictions-on-collectible-assemblies"></a>Restrições em assemblies de coleção

As seguintes restrições se aplicam a assemblies de coleção: 

- **Referências estáticas**   
  Tipos em um assembly dinâmico comum não podem ter referências estáticas para tipos que são definidos em um assembly de coleção. Por exemplo, se você definir um tipo comum que herda de um tipo em um assembly de coleção, um <xref:System.NotSupportedException> exceção será lançada. Um tipo em um assembly de coleção pode ter referências estáticas para um tipo em outro assembly de coleção, mas isso aumenta o tempo de vida do assembly referenciado para o tempo de vida do assembly de referência.

- **Interoperabilidade COM**   
   Nenhuma interfaces COM podem ser definidos em um assembly de coleção e não há instâncias de tipos em um assembly de coleção podem ser convertidas em objetos COM. Um tipo em um assembly de coleção não pode servir como um invólucro (CCW) ou (RCW) runtime callable wrapper. No entanto, os tipos em assemblies de coleção podem usar objetos que implementam interfaces COM.

- **Invocação de plataforma**   
   Os métodos que possuem o <xref:System.Runtime.InteropServices.DllImportAttribute> atributo não será compilado quando eles são declarados em um assembly de coleção. O <xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType> instrução não pode ser usada na implementação de um tipo em um assembly de coleção e não podem ser empacotados esses tipos para código não gerenciado. No entanto, você pode chamar código nativo por meio de um ponto de entrada que é declarado em um assembly de coleção.
 
- **Realização de marshaling**   
   Objetos (em particular, delegados) que são definidos em assemblies de coleção não podem ser empacotados. Esta é uma restrição em todos os tipos de emitido transitórios.

- **Carregamento do assembly**   
   Emissão de reflexão é o único mecanismo que tem suporte para o carregamento de assemblies de coleção. Assemblies são carregados por meio de qualquer outra forma de carregamento do assembly não podem ser descarregados.
 
- **Objetos associados ao contexto**    
   Não há suporte para variáveis de contexto estático. Não é possível estender tipos em um assembly de coleção <xref:System.ContextBoundObject>. No entanto, o código em assemblies de coleção pode usar objetos associados a contexto que são definidos em outro lugar.

- **Dados de thread estático**       
   Não há suporte para variáveis de thread estático.

## <a name="see-also"></a>Consulte também

[Emissão de métodos e assemblies dinâmicos](emitting-dynamic-methods-and-assemblies.md)
