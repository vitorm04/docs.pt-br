### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a>Verificação ortográfica do WPF em controles habilitados por texto não funcionará no Windows 10 para idiomas que não estão na lista de idiomas de entrada do sistema operacional

|   |   |
|---|---|
|Detalhes|Ao ser executado no Windows 10, o verificador ortográfico pode não funcionar em controles habilitados por texto do WPF, pois as funcionalidades da plataforma de verificação ortográfica estão disponíveis somente para os idiomas presentes na lista de idiomas de entrada. No Windows 10, quando um idioma é adicionado à lista de teclados disponíveis, o Windows baixa e instala automaticamente um pacote FOD (Recurso sob Demanda) que oferece as funcionalidades de verificação ortográfica. Ao adicionar o idioma à lista de idiomas de entrada, o verificador ortográfico terá suporte.|
|Sugestão|Lembre-se de que o idioma ou texto a ser verificado ortograficamente precisa ser adicionado como idioma de entrada para a verificação ortográfica funcionar no Windows 10.|
|Escopo|Microsoft Edge|
|Versão|4.6|
|Tipo|Tempo de execução|

