# Guia de contribuição

Este repositório é baseado em Git, contendo arquivos de tradução no
formato .po do padrão GNU Gettext. Por esse motivo, busque se
familiarizar com essas tecnologias, visto que este guia não tem a
intenção de ser exaustivo nas instruções sobre essas tecnologias.

## Glossário

**GNU Gettext**
é um conjunto de ferramentas e padrões que fornece ao desenvolvimento
e à tradução recursos que possibilitam e facilitam produção de
programas multilíngues.

**arquivo .po**, **arquivo de tradução**
é um arquivo texto no formato **GNU Gettext** no qual o tradutor aplica
a tradução para seu idioma alvo a partir das mensagens de origem,
em inglês, que foram extraídas de arquivos do código-fonte.

**arquivo .pot**
é um arquivo texto no formato **GNU Gettext** que armazena mensagens
fonte, em inglês, e serve de modelo, base, para gerar um ou atualizar
mensagens fonte em **arquivo .po** de cada idioma. Não deve ser traduzido.

**editor de texto**
é um programa para editar texto genérico, ou seja, que não tenha
tratamento específicos para tradução de **arquivos .po**, excluindo-se
realce de sintaxe, mas que ainda sim podem ser úteis.
Exemplo: vim, nano, Gedit, Kate, Notepad++.

**editor especializado**
é um programa com suporte especializado para edição de **arquivos .po**
(além de suporte a outros formatos de tradução), que agilize a trabalho
de tradução evitando a preocupação com problemas simples de sintaxe do
padrão GNU Gettext.

**placeholder**
é uma variável usada em mensagens de **arquivo .po** que o programa ao
da tradução vai, em tempo de execução, substituir por um valor dado. <br/>
Exemplo de **placeholders**: `%s`, `%d`, `%zu`, `%llu` em arquivos
c-format ou python, {} em python, `~a` em guile. <br/>
Exemplo de cenário, a mensagem no **arquivo .po** "Size: %s", no qual o programa
substitui "%s" por "10 GiB", resultaria "Size: 10 GiB"

**fork**, **branch**, **merge**
são termos relacionados ao sistema de controle de
versão Git. Veja explicação desses e outros termos na
[página gitglossary do Git](https://git-scm.com/docs/gitglossary) ou
executando `man gitglossary` na linha de comando.

**merge request**
é um termo do GitLab para um mecanismo de colaboração de código,
permitindo discussão, visualização das alterações ('diff') dos
commits, e mais. Vide
[Merge Request](https://docs.gitlab.com/ee/user/project/merge_requests/)
para mais informações.

**WIP**
é um acrônimo para Work In Progress, que em português significa
"trabalho em progresso". Ao colocar "WIP:" no início do título de
um **merge request** está bloqueando o **merge**, pois significa que
esta merge request não está pronta para se fazer um **merge**,
ou seja, ainda necessita de ajustes para se juntar ao código-fonte
do **branch** _master_.

## Licença

As contribuições aos arquivos tradução estão sujeitas às mesmas licenças
dos programas originais, conforme expresso nos próprios arquivos .po

## Fluxo de trabalho

O fluxo padrão é:

1. Faça um **fork** deste repositório
2. Crie um novo **branch**, com nome sugestivo
3. Crie uma **merge request** com descrição iniciada com **WIP:**
4. Neste novo **branch**, traduza o arquivo .po desejado
5. Ao final, remova **WIP:** do título para permitir o **merge**

Veja como realizar esses simples passos no [guia de atividades básicas do GitLab](https://docs.gitlab.com/ee/gitlab-basics/README.html).

## Tradução do arquivo .po

### Inicializando uma tradução

Caso um arquivo .po não tenha sido disponibilizado, é necessário primeiro
inicializar um. Para isto, é necessário obter o arquivo .pot do projeto,
sendo que a forma de obtenção ou de onde varia para cada projeto, e então
executar

```
msginit -i <arquivo .pot> -o <arquivo .po>
```

sendo `-i` usado para informar o arquivo de entrada e `-o` o arquivo de
saída. Ao final, arquivo .po terá sido criado.

**Dica:** O Poedit tem o recurso de gerar arquivos .po a partir do arquivo .pot
em sua própria interface gráfica.

### Traduzindo

Aqui entra o uso de um **editor especializado** e da preenchimento do
arquivo .po com a tradução.

Usando algum **editor especializado**, deve-se abrir o **arquivo .po** e
ir traduzindo cada mensagem fonte.

Veja abaixo algumas observações importantes:

#### Atenção ao contexto da mensagem

O contexto em que a mensagem é usada pode fazer total diferença na forma
como ela é traduzida. Certifique-se de identificar o contexto, ainda que
tenha que ler o código-fonte para eliminar eventual dúvida.
    
#### Atenção para pontuação

Algum simples e fácil de se esquecer, o ponto final pode ser parte
importante da mensagem, e sua falta, caso exista na mensagem original,
pode prejudicar a qualidade de tradução.
    
#### Atenção aos placeholders

Embora a falta de um **placeholder** ser alertada por um **editor
especializado**, seu mau posicionamento na  mensagem traduzida não
é alertado. Busque entender o contexto em que ele é posicionado
para colocar em um lugar correto. Por exemplo: na mensagem
"%s translation", o que é %? Poderia ser a quantidade "1 translation",
ou adjetivo "good translation", nome de um projeto "MyProj translation".

#### Mantenha a consistência

É comum termos serem repetidos ao longo de todo o arquivo .po, ou
entre vários arquivos .po deste mesmo projeto. Certifique-se de
buscar manter uma consistência sempre, para não confundir o usuário
na interface traduzida. Por exemplo, "contributor" pode ser traduzido
como "colaborador" ou "contribuidor". Escolha um e siga para o resto
do uso dessa palavra para esse contexto.
