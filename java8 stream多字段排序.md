List<类> list; 

 

//返回 对象集合以类字段一升序排序

 

list.stream().sorted(Comparator.comparing(类::字段一));

 

//返回 对象集合以类字段一降序排序 注意两种写法

 

list.stream().sorted(Comparator.comparing(类::字段一).reversed());//先以字段一升序,结果进行字段一降序

 

list.stream().sorted(Comparator.comparing(类::字段一,Comparator.reverseOrder()));//以字段一降序

 

//返回 对象集合以类字段一升序 字段二升序

 

list.stream().sorted(Comparator.comparing(类::字段一).thenComparing(类::字段二));

 

//返回 对象集合以类字段一降序 字段二升序 注意两种写法

 

list.stream().sorted(Comparator.comparing(类::字段一).reversed().thenComparing(类::字段二));//先以字段一升序,升序结果进行字段一降序,再进行字段二升序

 

list.stream().sorted(Comparator.comparing(类::字段一,Comparator.reverseOrder()).thenComparing(类::字段二));//先以字段一降序,再进行字段二升序

 

//返回 对象集合以类字段一降序 字段二降序 注意两种写法

 

list.stream().sorted(Comparator.comparing(类::字段一).reversed().thenComparing(类::字段二,Comparator.reverseOrder()));//先以字段一升序,升序结果进行字段一降序,再进行字段二降序

 

list.stream().sorted(Comparator.comparing(类::字段一,Comparator.reverseOrder()).thenComparing(类::字段二,Comparator.reverseOrder()));//先以字段一降序,再进行字段二降序

 

//返回 对象集合以类字段一升序 字段二降序 注意两种写法

 

list.stream().sorted(Comparator.comparing(类::字段一).reversed().thenComparing(类::字段二).reversed());//先以字段一升序,升序结果进行字段一降序,再进行字段二升序,结果进行字段一降序字段二降序

 

list.stream().sorted(Comparator.comparing(类::字段一).thenComparing(类::字段二,Comparator.reverseOrder()));//先以字段一升序,再进行字段二降序<br><br><br>


 public static void main(String[] args) {


        List<ArticleVO> articleVOS = new ArrayList<>();
        ArticleVO build0 = ArticleVO.builder().postTime("20200101").pageViewCount("3").build();
        ArticleVO build1 = ArticleVO.builder().postTime("20200102").pageViewCount("5").build();
        ArticleVO build2 = ArticleVO.builder().postTime("20200101").pageViewCount("7").build();
        ArticleVO build3 = ArticleVO.builder().postTime("20200102").pageViewCount("6").build();
        ArticleVO build4 = ArticleVO.builder().postTime("20200103").pageViewCount("4").build();
        ArticleVO build5 = ArticleVO.builder().postTime("20200104").pageViewCount("2").build();
        ArticleVO build6 = ArticleVO.builder().postTime("20200105").pageViewCount("2").build();
        articleVOS.add(build0);
        articleVOS.add(build1);
        articleVOS.add(build2);
        articleVOS.add(build3);
        articleVOS.add(build4);
        articleVOS.add(build5);
        articleVOS.add(build6);
//        Comparator<Object> comparing = Comparator.comparing(ArticleVO::getPostTime);
//        comparing.thenComparing(ArticleVO::getPostTime).thenComparing(ArticleVO::getPageViewCount);
        List<ArticleVO> collect = articleVOS.stream().sorted(Comparator.comparing(ArticleVO::getPostTime,Comparator.reverseOrder())
                .thenComparing(ArticleVO::getPageViewCount,Comparator.reverseOrder())).collect(Collectors.toList());
        System.out.println(collect);
    }
