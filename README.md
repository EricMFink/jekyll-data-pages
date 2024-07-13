# Jekyl Data Pages Generator 

_Forked from [avillafiorita/jekyll-datapage_gen](https://github.com/avillafiorita/jekyll-datapage_gen)_

## Configuration

Add to ```_config.yml```: 


```
page_gen-dirs: [true|false]

page_gen:
- data: [name of YAML file in ```_data```]
  template: [name of template in ```_layouts``` used to render pages]
  dir: [directory where pages will be generated; default = same as _data_]
  name: [field in data file used to generate page filenames]
  title: [field in data file used to generate page titles; default = same as _name_]
  extension: [extension used to generate the filename; default = html]
  filter: [property to filter data records by]
  filter_condition: [Ruby expression to filter data]
  page_data_prefix: [prefix used to name variables]

```  

For YAML files with hierarchically structured data, use full path to specify desired subset. For example, using a file named ```_data/books.yml```:

```
fiction: 
- author: Franz Kafka
  title: Der Process (The Trial)
  date: 1914-15
- author: Jaroslav Hašek
  title: The Good Soldier Švejk
  date: 1921-23
- author: Robert Musil
  title: The Man Without Qualities 
  date: 1930, 1933, 1943

non-fiction: 
- author: Walter Benjamin
  title: Berliner Chronik (Berlin Chronicle)
  date: 2019
- author: Gershom Scholem
  title: Walter Benjamin: the Story of a Friendshi
  date: 1981
- author: Moishe Postone
  title: Time, Labor and Social Domination: A Reinterpretation of Marx's Critical Theory.
  date: 1993

```

To generate pages for items under "fiction": 

### Additional fields (optional)

- index_files: [true|false]; overrides value of _page_gen-dirs_
- filter: a property of each data record that must return a
  true-ish value for the record to be included in the list of files to
  be generated.
  See [[Filtering Data]], below, for more details.
  /Optional: if not specified, all records from the dataset are included (see also _filter_condition_)./
- filter_condition: a string containing a Ruby expression which evaluates
  to a true-ish value. The condition can reference fields of the data being
  read using the _record_ hash (e.g., _record['author'] __ 'George
  Orwell'_).
  See [[Filtering Data]], below, for more details.
  /Optional: if not specified, all records from the dataset are included (see also _filter_)./
- debug: a Boolean value specifying whether the plugin will output information
  about the configuration and data read.
  /Optional: if not specified, no debug information is outputted./

A liquid tag is also made available to generate a link to a given page.
For instance ```{{ page_name | datapage_url: dir }}``` generates a link to _page_name_ in _dir_.

See [avillafiorita/jekyll-datapage_gen](https://github.com/avillafiorita/jekyll-datapage_gen) further explanation.


## License

Distributed under the terms of the [[http://opensource.org/licenses/MIT][MIT License]].