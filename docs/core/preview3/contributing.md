# <a name="using-the-cli-preview3-folder-and-sub-folders"></a>Usando a pasta cli-preview3 e subpastas

Essa pasta é o nó de nível superior que corresponde à pasta ferramentas, mas contém deltas para a versão de Visualização 3 das ferramentas do .NET Core.

O objetivo dessa estrutura separada de pasta paralela é fornecer um local para o conteúdo relacionado à versão da Visualização 3, que pode ser mesclado com relativa facilidade à estrutura principal ao fornecer versão de alternância no site publicado.

O conteúdo desse nó deve ser um conjunto menor de documento que representa os deltas da versão de Suporte a Longo Prazo (LTS) e a última versão atual. 

## <a name="structure"></a>Estrutura

Há dois casos para a adição de novo conteúdo para essa versão:

* Alterações nos documentos existentes
    - Copie o conteúdo existente para uma pasta paralela nessa estrutura. Faça as alterações e adicione o arquivo modificado ao sumário para a versão de Visualização 3.
* Novos documentos
    - Coloque o novo documento no local apropriado e adicione-o ao sumário sob o nó para a versão de Visualização 3. 

Todos os arquivos da versão atual devem ter o seguinte adicionado à parte superior do tópico:

[!include[current release track](../includes/warning.md)]

Criamos um trecho de código para incluir com a seguinte sintaxe:

```markdown
[!include[current release track](../../includes/warning.md)]
```

### <a name="link-instructions"></a>Instruções de link

Em ambos os casos, forneça links da versão atual à página LTS (ou index.md pai) para fins de navegação.
Considere fornecer links da página LTS (ou index.md pai) à nova página de conteúdo da versão atual.

## <a name="future-considerations"></a>Considerações futuras

Nossa meta final é que diferentes versões apareçam como ramificações no [repositório de documentos](https://github.com/dotnet/docs). Até que se ofereça suporte a esse cenário de publicação, utilizaremos pastas de nível superior diferentes para cada versão atual. 

Na hora certa, será possível mesclar cada versão atual na pasta principal [documentos](../docs), mesclar os nós de sumário e publicá-los como um conjunto separado de documentos. Talvez seja necessário mesclar modificações na versão LTS e na versão atual de um arquivo, mas será possível encontrar essas alterações com relativa facilidade.


<!--HONumber=Nov16_HO3-->


