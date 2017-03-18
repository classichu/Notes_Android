# Dom  基于文档结构

一次性加载xml文件，再使用DOM的 api去进行解析，这样很大程度的消耗内存。
优点语法简单，结构明显

## 写入文件
1 取得文本构建工厂
DocumnetBuilderFactory factory=DocumnetBuilderFactory.newInstance();
2 取得文本构建
DocumnetBuilder builder=factory.newDocumnetBuilder();
3 创建文本
Doucment doc=builder.newDocumnet();
4 创建元素

element1.appendChild(document.createTextNode("node1"));
           element2.appendChild(element3);
           element1.appendChild(element2);

           document.appendChild(element1);

... ...


## 读取

1 取得文本构建工厂
DocumnetBuilderFactory factory=DocumnetBuilderFactory.newInstance();
2 取得文本构建
DocumnetBuilder builder=factory.newDocumnetBuilder();
3 取得文本从文件流中
Document dom = dombuild.parse(instream)

4  通过获取 getElementsXXX方法得到  配合列表遍历



      ```
      public List<Person> getPersons(InputStream stream) throws Throwable
       {
        List<Person> list =new ArrayList<Person>();
        DocumentBuilderFactory factory =DocumentBuilderFactory.newInstance();
        DocumentBuilder builder =factory.newDocumentBuilder();
       Document dom = builder.parse(stream);//解析完成，并以dom树的方式存放在内存中。比较消耗性能
        //开始使用dom的api去解析
        Element root = dom.getDocumentElement();//根元素
       NodeList personNodes = root.getElementsByTagName("person");//返回所有的person元素节点
       //开始遍历啦
       for(int i=0;i<personNodes.getLength();i++)
       {
        Person person =new Person();
       Element personElement =(Element)personNodes.item(i);
         person.setId(new Integer( personElement.getAttribute("id")));//将person元素节点的属性节点id的值，赋给person对象
         NodeList personChildrenNodes =personElement.getChildNodes();//获取person节点的所有子节点
         //遍历所有子节点
         for(int j=0;j<personChildrenNodes.getLength();j++)
         {
          //判断子节点是否是元素节点（如果是文本节点，可能是空白文本，不处理）
          if(personChildrenNodes.item(j).getNodeType()==Node.ELEMENT_NODE)
          {
           //子节点--元素节点
           Element childNode =(Element)personChildrenNodes.item(j);
              if("name".equals(childNode.getNodeName()))
              {
               //如果子节点的名称是“name”.将子元素节点的第一个子节点的值赋给person对象
               person.setName(childNode.getFirstChild().getNodeValue());

              }else if("age".equals(childNode.getNodeValue()))
              {
               person.setAge(new Integer(childNode.getFirstChild().getNodeValue()));
              }
          }

         }
         list.add(person);
       }
       return list;
       }
       ```



# SAX  基于事件流驱动  
系统负责得到事件
从文件的开始顺序解析到文档的结束，不可暂停或倒退

## 解析
1 创建SAX解析工厂
2 创建SAX解析器
3 创建解析DefaultHandler（ContentHandler）继承类
     继承类里覆盖  startDocument    endDocument   startElement endElement   characters
    等方法 在方法里处理保存相应元素的数据  

4 解析器注册这个DefaultHandler
... ...

# pull  基于事件驱动
自己实现读取得到事件

读取到xml的声明返回 START_DOCUMENT;

读取到xml的结束返回 END_DOCUMENT ;

读取到xml的开始标签返回 START_TAG

读取到xml的结束标签返回 END_TAG

读取到xml的文本返回 TEXT
