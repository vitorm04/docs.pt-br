---
title: "Instruções: adicionar e remover itens de um ConcurrentDictionary| Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- thread-safe collections, concurrent dictionary
ms.assetid: 81b64b95-13f7-4532-9249-ab532f629598
caps.latest.revision: 13
author: mairaw
ms.author: mairaw
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9d20d75b2492c214305c07a5e19941cd91b66f67
ms.lasthandoff: 04/18/2017

---
# <a name="how-to-add-and-remove-items-from-a-concurrentdictionary"></a>Como adicionar e remover itens de um ConcurrentDictionary
Este exemplo mostra como adicionar, recuperar, atualizar e remover itens de um <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName>. Essa classe de coleção é uma implementação thread-safe. É recomendável usá-la sempre que vários threads possam estar tentando acessar os elementos simultaneamente.  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> fornece vários métodos de conveniência que eliminam a necessidade de que o código primeiro verifique se existe uma chave antes de tentar adicionar ou remover dados. A tabela a seguir lista esses métodos de conveniência e descreve quando usá-los.  
  
|Método|Use quando…|  
|------------|---------------|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>|Você desejar adicionar um novo valor para uma chave especificada e, se a chave já existir, você desejar substituir seu valor.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>|Você desejar recuperar o valor existente de uma chave especificada e, se a chave não existir, você desejar especificar um par chave/valor.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A>|Você desejar adicionar, obter, atualizar ou remover um par chave/valor e, se a chave já existir ou se a tentativa falhar por qualquer motivo, você desejar executar alguma ação alternativa.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa duas instâncias de <xref:System.Threading.Tasks.Task> para adicionar alguns elementos em um <xref:System.Collections.Concurrent.ConcurrentDictionary%602> simultaneamente e, em seguida, gera todo o conteúdo para mostrar que os elementos foram adicionados com êxito. O exemplo também mostra como usar os métodos <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>, <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> e <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> para adicionar, atualizar e recuperar itens da coleção.  
  
 [!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
 [!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]  
  
 O <xref:System.Collections.Concurrent.ConcurrentDictionary%602> foi desenvolvido para cenários multi-threaded. Você não precisa usar bloqueios em seu código para adicionar ou remover itens da coleção. No entanto, sempre é possível que um thread recupere um valor e que outro thread atualize imediatamente a coleção, dando um novo valor à mesma chave.  
  
 Além disso, embora todos os métodos de <xref:System.Collections.Concurrent.ConcurrentDictionary%602> sejam thread-safe, nem todos os métodos são atômicos, especificamente o <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> e o <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>. O delegado do usuário que é passado para esses métodos é invocado fora do bloqueio interno do dicionário. (Isso é feito para impedir que um código desconhecido bloqueie todos os threads.) Portanto, é possível que essa sequência de eventos ocorra:  
  
 1\) threadA chama <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>, não localiza nenhum item e cria um novo item para adicionar, invocando o delegado valueFactory.  
  
 2\) threadB chama <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> simultaneamente, seu delegado de valueFactory é invocado e chega ao bloqueio interno antes de threadA e, em seguida, seu novo par chave-valor é adicionado ao dicionário.  
  
 3\) o delegado do usuário de threadA é concluído e o thread chega ao bloqueio, mas agora vê que o item já existe  
  
 4\) threadA executa um "Get" e retorna os dados que foram adicionados anteriormente por threadB.  
  
 Portanto, não é garantido que os dados retornados por <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> sejam os mesmos dados que foram criados por valueFactory do thread. Uma sequência de eventos semelhante pode ocorrer quando <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> é chamado.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Collections.Concurrent?displayProperty=fullName>   
 [Coleções Thread-Safe](../../../../docs/standard/collections/thread-safe/index.md)
