# 2022graphics
```c++
#include <GL/glut.h>
void display()
{
    glClear( GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT );
    glColor3f(1,1,0);
    glutSolidTeapot(0.3);
    glutSwapBuffers();
}
int main(int argc,char**argv)
{
    glutInit(&argc,argv);
    glutInitDisplayMode(GLUT_DOUBLE | GLUT_DEPTH);
    glutCreateWindow("week03的視窗");
    glutDisplayFunc(display);
    glutMainLoop();
    return 0;
}

```
```c++
#include <GL/glut.h>
void display()
{
    glClear( GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT );
    glColor3f(1,1,0);
     glBegin(GL_TRIANGLES);

                glColor3f(1.0f, 0.0f, 0.0f);   glVertex2f(0.0f,   1.0f);
                glColor3f(0.0f, 1.0f, 0.0f);   glVertex2f(0.87f,  -0.5f);
                glColor3f(0.0f, 0.0f, 1.0f);   glVertex2f(-0.87f, -0.5f);

            glEnd();
    glutSwapBuffers();
}
int main(int argc,char**argv)
{
    glutInit(&argc,argv);
    glutInitDisplayMode(GLUT_DOUBLE | GLUT_DEPTH);
    glutCreateWindow("week03的彩色三角形視窗");
    glutDisplayFunc(display);
    glutMainLoop();
    return 0;
}

```
```c++
#include <GL/glut.h>
#include <stdio.h>
int mouseX=0,mouseY=0,N=0;
int mx[100],my[100];
void display()
{
    glClear( GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT );
    glColor3f(1,1,0);
    glBegin(GL_LINE_LOOP);
        for(int i=0;i<N;i++){
            glVertex2f((mx[i]-150)/150.0,-(my[i]-150)/150.0);
        }
    glEnd();
    glutSwapBuffers();
}
void mouse(int button,int state,int x,int y)
{
    mouseX=x; mouseY=y;
    if(state==GLUT_DOWN){
        printf("    glVertex2f( (%d-150)/150.0,-(%d-150)/150.0);\n",x,y);
        N++;
        mx[N-1]=x; my[N-1]=y;
    }
}
int main(int argc,char**argv)
{
    glutInit(&argc,argv);
    glutInitDisplayMode(GLUT_DOUBLE | GLUT_DEPTH);
    glutCreateWindow("week04 mouse");

    glutDisplayFunc(display);
    glutMouseFunc(mouse);
    glutMainLoop();
    return 0;
}
```
```c++
#include <GL/glut.h>
void myTeapot(float x,float y)
{
    glPushMatrix();
        glTranslatef(x,y,0);
        glutSolidTeapot(0.3);
    glPopMatrix();
}
void display()
{
    glClear( GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT );
    glColor3f(1,0,0);
    myTeapot(+0.5,+0.5);
    myTeapot(+0.5,-0.5);
    myTeapot(-0.5,+0.5);
    myTeapot(-0.5,-0.5);

    glutSwapBuffers();
}
int main(int argc,char**argv)
{
    glutInit(&argc,argv);
    glutInitDisplayMode(GLUT_DOUBLE | GLUT_DEPTH);
    glutCreateWindow("week04 translate");
    glutDisplayFunc(display);
    glutMainLoop();
    return 0;
}
```
```c++
#include <GL/glut.h>
#include <stdio.h>
int N=0;
int x[1000],y[1000];
void display()
{
    glClear( GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT );
    glBegin(GL_LINE_LOOP);
        for(int i=0;i<N;i++){
            glVertex2f((x[i]-150)/150.0,-(y[i]-150)/150.0);
        }
    glEnd();
    glutSwapBuffers();
}
//void mouse(int button,int state,int mouseX,int mouseY)
void motion(int mouseX,int mouseY)
{
    //if(state==GLUT_DOWN){
        N++;
        x[N-1]=mouseX;
        y[N-1]=mouseY;
        printf("現在按下滑鼠,得到新座標 %d %d\n",x[N-1],y[N-1]);
    //}
    display();
}
int main(int argc,char**argv)
{
    glutInit(&argc,argv);
    glutInitDisplayMode(GLUT_DOUBLE | GLUT_DEPTH);
    glutCreateWindow("week04 mouse");

    glutDisplayFunc(display);
    glutMotionFunc(motion);
    glutMainLoop();
    return 0;
}
```
```c++
#include <GL/glut.h>
float angle=0, oldX=0;
void display()
{
    glClear( GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT );
    glPushMatrix();
    glRotatef(angle,0,0,1);
    glColor3f(1,1,0);
    glutSolidTeapot(0.3);
    glPopMatrix();
    glutSwapBuffers();
}
void mouse(int button,int state,int x,int y)
{
    oldX=x;
}
void motion(int x,int y)
{
    angle+=(x-oldX);
    oldX=x;
    display();
}
int main(int argc,char**argv)
{
    glutInit(&argc,argv);
    glutInitDisplayMode(GLUT_DOUBLE | GLUT_DEPTH);
    glutCreateWindow("week05 Rotate");
    glutDisplayFunc(display);
    glutMouseFunc(mouse);
    glutMotionFunc(motion);
    glutMainLoop();
    return 0;
}
```
```c++
#include <GL/glut.h>
float angle=0;
void display()
{
    glClear( GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT );
    glPushMatrix();
    glRotatef(angle,0,0,1);
    glColor3f(1,1,0);
    glutSolidTeapot(0.3);
    glPopMatrix();
    glutSwapBuffers();
}
void motion(int x,int y)
{
    angle=x;
    display();
}
int main(int argc,char**argv)
{
    glutInit(&argc,argv);
    glutInitDisplayMode(GLUT_DOUBLE | GLUT_DEPTH);
    glutCreateWindow("week05 Rotate");
    glutDisplayFunc(display);
    glutMotionFunc(motion);
    glutMainLoop();
    return 0;
}

```
```c++
#include <GL/glut.h>
#include <stdio.h>
void display()
{
    glClear( GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT );
        glColor3f(1,1,0);
        glutSolidTeapot(0.3);
    glutSwapBuffers();
}
void keyboard( unsigned char key,int x,int y)
{
    printf("現在按下:%c 座標在:%x %x\n",key,x,y);
}
int main(int argc,char**argv)
{
    glutInit(&argc,argv);
    glutInitDisplayMode(GLUT_DOUBLE | GLUT_DEPTH);
    glutCreateWindow("week06 keyboard");
    glutDisplayFunc(display);
    glutKeyboardFunc(keyboard);
    glutMainLoop();
    return 0;
}

```
```c++
#include <GL/glut.h>
#include <stdio.h>
float x=0,y=0,z=0,oldX,oldY;
void display()
{
    glClear( GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT );
    glPushMatrix();
    glTranslatef((x-150)/150.0,-(y-150)/150.0,z);
        glColor3f(1,1,0);
        glutSolidTeapot(0.3);
    glPopMatrix();
    glutSwapBuffers();
}
void keyboard( unsigned char key,int mouseX,int mouseY)
{
    printf("現在按下:%c 座標在:%x %x\n",key,mouseX,mouseY);
}
void mouse(int button,int state,int mouseX,int mouseY)
{
    oldX=mouseX; oldY=mouseY;
}
void motion(int mouseX,int mouseY)
{
    x+=(mouseX-oldX);
    y+=(mouseY-oldY);
    oldX=mouseX; oldY=mouseY;
    display();
}
int main(int argc,char**argv)
{
    glutInit(&argc,argv);
    glutInitDisplayMode(GLUT_DOUBLE | GLUT_DEPTH);
    glutCreateWindow("week06 keyboard mouse motion");
    glutDisplayFunc(display);
    glutKeyboardFunc(keyboard);
    glutMouseFunc(mouse);
    glutMotionFunc(motion);
    glutMainLoop();
    return 0;
}

```
