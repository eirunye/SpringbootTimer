# SpringbootTimer
  
  ### 1、Spring boot 定时器的运用
      
  >主要是添加注解的方式进行
      
         
          1、在Application中添加
          @MapperScan("com.example.myjpa.dao")//mybatis的注解
          @EnableScheduling//定时器注解
          
          2、创建 ScheduledTasks.class
          添加注解：
          @Configuration //1.主要用于标记配置类，兼备Component的效果。
          @EnableScheduling // 2.开启定时任务
          
          3、创建config定时器配置 CompleteScheduleConfig.class
          @Configuration
          @EnableScheduling
          
          4、代码如下：
          
          private static String DEFAULT_CRON = "0 0/2 * * * ?";//表示间隔2分钟
          //cron的时间间隔语法：0 0/2 * * * ?;
          @Override
          public void configureTasks(ScheduledTaskRegistrar scheduledTaskRegistrar) {

          //        scheduledTaskRegistrar.scheduleFixedDelayTask(new FixedDelayTask(() -> {
          //
          //        }, 10000, 1000 * 60));

          scheduledTaskRegistrar.addTriggerTask(() -> {
            Student student = new Student();
            student.setName("ok");
            student.setAge(12);
            student.setSex("nan");
            studentRepository.save(student);//jpa插入数据
          }, triggerContext -> {
            return new CronTrigger(DEFAULT_CRON).nextExecutionTime(triggerContext);
          });
          }
          
          
  ### 2、Spring boot 在定时器中进行数据库操作，在jpa框架进行增删改查操作数据库
  
  >数据库操作
      
        1、简单的增删改查
  
  ### 3、Spring boot mybatis 的简单运用
  
  >mydatis的简单运用
  
        1、之后会更新更多关于mybatis的案例
  
